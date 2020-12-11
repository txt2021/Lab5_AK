НАЦІОНАЛЬНИЙ ТЕХНІЧНИЙ УНІВЕРСИТЕТ УКРАЇНИ 

«КИЇВСЬКИЙ ПОЛІТЕХНІЧНИЙ ІНСТИТУТ»

ФАКУЛЬТЕТ ІНФОРМАТИКИ І ОБЧИСЛЮВАЛЬНОЇ ТЕХНІКИ

КАФЕДРА ОБЧИСЛЮВАЛЬНОЇ ТЕХНІКИ








Лабораторна робота №5

з дисципліни «Архітектура комп’ютерів 2»








Виконала:

студентка 3 курсу 

групи ІВ-82

Чуясова Тетяна


Перевірив: 

Нікольський С. С.












Київ 2020 р.

Лістинг програми:

hello.c 

/*
 * Copyright (c) 2017, GlobalLogic Ukraine LLC
 * All rights reserved.
 *
 * Redistribution and use in source and binary forms, with or without
 * modification, are permitted provided that the following conditions are met:
 * 1. Redistributions of source code must retain the above copyright
 *    notice, this list of conditions and the following disclaimer.
 * 2. Redistributions in binary form must reproduce the above copyright
 *    notice, this list of conditions and the following disclaimer in the
 *    documentation and/or other materials provided with the distribution.
 * 3. All advertising materials mentioning features or use of this software
 *    must display the following acknowledgement:
 *    This product includes software developed by the GlobalLogic.
 * 4. Neither the name of the GlobalLogic nor the
 *    names of its contributors may be used to endorse or promote products
 *    derived from this software without specific prior written permission.
 *
 * THIS SOFTWARE IS PROVIDED BY GLOBALLOGIC UKRAINE LLC `AS IS` AND ANY
 * EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED
 * WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE
 * DISCLAIMED. IN NO EVENT SHALL GLOBALLOGIC UKRAINE LLC BE LIABLE FOR ANY
 * DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES
 * (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES;
 * LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND
 * ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT
 * (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS
 * SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.
 */

#include <linux/init.h>

#include <linux/module.h>

#include <linux/moduleparam.h>

#include <linux/printk.h>

MODULE_AUTHOR("Chuiasova Tetiana IV-82");

MODULE_DESCRIPTION("Hello world (Linux module)");

MODULE_LICENSE("Dual BSD/GPL");

static int repeat = 1;

module_param(repeat, uint, S_IRUGO);

MODULE_PARM_DESC(times, "repeat amount");

static int __init hello_init(void)

{

    uint i = 0;
    
    if(repeat == 0) {
    
        printk(KERN_WARNING "Repetition parameter = 0");  
        
    } else if(repeat >= 5 && repeat <= 10) {
    
        printk(KERN_WARNING "Repetition parameter is between 5 and 10");
        
    } else if(repeat > 10) {
    
        printk(KERN_ERR "Repetition parameter > 10");
        
        return -EINVAL;
        
    }
    
    for(i = 0; i < repeat; i++) {
    
        printk(KERN_EMERG "Hello, world!\n");
        
    }
    
    printk(KERN_INFO "Repeat: %d\n", repeat);
    
    return 0;
    
}

static void __exit hello_exit(void)

{

    /* Do nothing here right now */
    
}

module_init(hello_init);

module_exit(hello_exit);




Результати виконання роботи та MakeFile можна подивиися, завантаживши файл звіту


