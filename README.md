###1. Числа Фибоначчи
Реализовать подсчет **N**-го числа фибоначчи двумя способами:
 1. последовательно(цикл + (массив|переменные для буфера)).
 2. **рекурсивно**.

 - Нужен метод для конкретного числа:
````javascript
console.log(fib(10)) // => 55
````

####Ссылки:
1. [Числа Фибоначчи](https://ru.wikipedia.org/wiki/%D0%A7%D0%B8%D1%81%D0%BB%D0%B0_%D0%A4%D0%B8%D0%B1%D0%BE%D0%BD%D0%B0%D1%87%D1%87%D0%B8)
2. [Рекурсия](https://ru.wikipedia.org/wiki/%D0%A0%D0%B5%D0%BA%D1%83%D1%80%D1%81%D0%B8%D1%8F#.D0.92_.D0.BF.D1.80.D0.BE.D0.B3.D1.80.D0.B0.D0.BC.D0.BC.D0.B8.D1.80.D0.BE.D0.B2.D0.B0.D0.BD.D0.B8.D0.B8)
3. [Javascript for](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/for)
 
- https://gist.github.com/odesskij/f0b02ee2872598fd00da

###2. Золотое сечение
####Описание:
  Маша любит Сашу, но мать Саши против их брака, т.к. она считает, что у Маши плохие пропорции лица. Помоги Саше переубедить мать относительно пропорций лица Маши с помощью золотого сечения.  
####Задание:
Реализовать подсчет значения [золотого сечения](https://ru.wikipedia.org/wiki/%D0%97%D0%BE%D0%BB%D0%BE%D1%82%D0%BE%D0%B5_%D1%81%D0%B5%D1%87%D0%B5%D0%BD%D0%B8%D0%B5) как отношения двух чисел Фибоначчи(из пункта 1.)
Чтобы было более убедительно, считать золотое сечение с точностью 10 знаков после десятичного разделителя.

- https://gist.github.com/odesskij/c2b124fc4a19a41cb377

###3. Событийная система
####Описание:
  Реализовать событийную систему.
  Необходимо реализовать объект у которого есть метод **trigger(event, [\*agrs])** (*1*),
  метод **on(event, callback, [context])** (*2*).
  Опционально реализовать еще метод **off(event, callback, [context])** (*3*)
  Если что-то не выйдет, я могу по частям разъяснить.

  - (1) -- метод, который провоцирует событие:
    * event -- имя события {String}
    * [\*agrs] -- необязательные аргумент, будут переданны в функцию обработчик(callback).
  - (2) -- метод для подписки на событие
    * event -- имя события {String}
    * callback -- обработчик {Function}
    * [context] -- необязательные агрумент, контекст в котором будет вызван callback. {Object}
  - (3) -- убирает обработчик событий (@see Backbone.Events). (Сигнатура как у (2))

####Как должно выглядеть и работать:
````javascript
  object.on('event', function(){
    var s = 0;
    for(var i=0; i<arguments.length; i++) {
      s += arguments[i];
    }

    console.log(s);
  });

  object.trigger('event', 1, 2, 3, 4); // => 10


  for(var i=0; i<3; i++) {
    (function(index){
      objectTwo.on('eventTwo', function(){
        console.log('event => ' + index);
      });
    })(i);
  }

  objectTwo.trigger('eventTwo');
    // => event => 0
    // => event => 1
    // => event => 2


  objectThree.on('eventThree', function(){
    console.log('random ' + this.random());
  }, Math);


  objectThree.trigger('eventThree');
    // => 0.5828531747683883

  objectThree.off('eventThree');

  objectThree.trigger('eventThree');
  //Ничего не произошло.
````

- https://gist.github.com/odesskij/b18bbdce73a63472b488

###4. Backbone.UserList
####Описание:
Страница с вкладками:
* Список пользователей (фото, имя, пол, город, дата регистрации(в данные она ввиде timestamp в поле registered, преобразовать к год/мес/день))
* Статистика по пользователам (кол-во пользователей из списка по gender и name.title mr|miss|и т.д.)
сделать бесшовный переход между в вкладками(SPA)
Все содержимое body строить на фронтенде, в качестве шаблонизатора лучше использовать _.template (http://underscorejs.org/#template)
Данные тянуть с сайта: https://randomuser.me/ (http://api.randomuser.me/?results=100)
Должно примерно получиться так: Backbone.Model для пользователя, Backbone.Collection для пользователя,
Одна общая Backbone.View которая строит изначальную структуру(список вкладок + контейнер для контента из них),
и еще две Backbone.View(ListView и StatView) для вкладок соответственно. + сделать кнопку для обновления данных с коллекции(UserCollection.fetch)
Нужные библиотеки(Backbone, Underscore) подтянуть как удобно. 
По желанию, использовать Backbone.Router для привязки вкладки к url(можно на последнюю очередь сделать)

####Ссылки:
http://underscorejs.org/ (http://underscorejs.ru/)
http://backbonejs.org/ (http://backbonejs.ru/)

-----------------
Каждое задание вылить на [github](https://github.com/) в ввиде отдельного [репозитория](https://help.github.com/articles/create-a-repo/).
