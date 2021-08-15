# ABSTRACT

Cвойства для навигации между узлами DOM
elem.parentNode - выберет родителя elem
elem.closest(любой селектор)- выберет ближайший elem с таким селектором
elem.childNodes - псевдомассив, хранит все дочерние элементы, включая текстовые.
elem.children - псевдомассив, хранит только дочерние узлы-элементы, то есть соответствующие тегам.
elem.firstChild - выберет первый дочерний элемент внутри elem, включая текстовые узлы.
elem.firstElementChild - выберет первый дочерний узел-элемент внутри elem.
elem.lastChild - выберет последний дочерний элемент внутри elem, включая текстовые узлы.
elem.lastElementChild - выберет последний дочерний узел-элемент внутри elem.
elem.previousSibling - выберет элемент "слева" от elem (его предыдущего соседа)
elem.previousElementSibling - выберет узел-элемент "слева" от elem (его предыдущего соседа)
elem.nextSibling - выберет элемент "справа" от elem (его следующего соседа)
elem.nextElementSibling - выберет узел-элемент "справа" от elem (его предыдущего соседа)
 свойства узлов DOM
    •  hidden - контролирует видимость элемента.
    • value - содержит текущий текстовый контент элементов input, select, textarea.
    • checked - хранит состояние чекбокса или радиокнопки.
    • name - хранит значение, указанное в HTML-атрибуте name.
    • src - путь к изображению тега <img>.
elem.textContent — свойство, содержит текстовый контент внутри элемента. 
HTMLElement.style -
        const button = document.querySelector('.btn')
                 button.style.backgroundColor = 'teal';

Методы для работы с классами элемента
    • elem.classList.contains(cls) - возвращает true или false в зависимости от того, есть ли у элемента класс cls
    • elem.classList.add(cls) - добавляет класс cls в список классов элемента
    • elem.classList.remove(cls) - удаляет класс cls из списка классов элемента
    • elem.classList.replace(oldClass, newClass) - заменяет существующий класс на указанный
    • elem.classList.toggle(cls) - если класса cls нет - добавляет его, если есть- удаляет
Атрибуты
    • elem.hasAttribute(name) - проверяет наличие аттрибута, возвращает true или false
    • elem.removeAttribute(name) - удаляет атрибут



      Создание DOM узла
const heading = document.createElement('h1');

heading.textContent = 'Привет! Я заголовок Н1';

или   elem.innerHTML = '<p class="text">Pellentesque habitant.</p>';
или метод insertAdjacentHTML() -метод парсит указанную строку как HTML и добавляет результирующие узлы в указанное место DOM-дерева. 
element.insertAdjacentHTML(position, string)
position — позиция относительно элемента. Принимает одно из следующих значений:
    • 'beforebegin' - перед element
    • 'afterbegin' - внутрь element, в самое начало контента
    • 'beforeend' - внутрь element, в самый конец контента
    • 'afterend' - после element

    • elem.insertAdjacentElement(position, elem) — вставляет в произвольное место не HTML-строку, а элемент elem.
    • elem.insertAdjacentText(position, text) — создаёт текстовый узел из строки text и вставляет его в указанное место относительно elem.

Методы append/prepend, before/after, replaceWith
    • parentElem.appendChild(elem) - добавляет elem в конец дочерних элементов parentElem.
    • parentElem.insertBefore(elem, nextSibling) - добавляет elem в коллекцию детей parentElem,     перед элементом nextSibling. Если вторым аргументом указать null, тогда insertBefore сработает как appendChild.
    • elem.append(nodes) - добавляет nodes в конец elem
    • elem.prepend(nodes) - добавляет nodes в начало elem
    • elem.after(nodes) - добавляет nodes после узла elem
    • elem.before(nodes) - добавляет nodes перед узлом elem
    • elem.replaceWith(nodes) - добавляет nodes вместо elem
Удаление узла - elem.remove()
Клонирование узла — elem.cloneNode(true)  (false, то копия будет сделана без дочерних элементов.)

Получаем все данные формы  «FormData»
const formEl = document.querySelector('.js-register-form');
formEl.addEventListener('submit', onFormSubmit);
function onFormSubmit (event) {
event.preventDefault(); - предотвращает перезагрузку страицы браузера
const formData = new FormData(event.currentTarget);
formData.forEach((name, value) => {
    console.log(name);
    console.log(value);})};

Получаем данные с инпута
const formData = event.currentTarget;
const numberID = formData.elements.query.value;

currentTarget – получает елемент, на котором вызванно событие.

СОБЫТИЯ ПОЛЕЙ ФОРМЫ

input – для текстовых полей;
const inputEl = document.querySelector('.js-input');
inputEl.addEventListener('input', onInput);
function onInput(event) {
         nameSpan.textContent = event.currentTarget.value};

change – для чекбоксов и радиобаттонов;

e.currentTarget.reset или element.reset();– сбрасывает все значение полей формы

У чекбоксов и радиобаттонов свойство checked. Буль, хранит чекнут или нет false/true.

ВСПЛЫТИЕ СОБЫТИЙ
currentTarget — это то на чем висит слушатель addEventListener
target – это елемент по которому мы кликнули;
if(e.target.nodeName !== 'BUTTON'){ - это границы обьекта по которому произведен клик.


ПЕРЕБОР В ЦИКЛЕ ЭЛЕМЕНТОВ DOM
const newArr = listItem.forEach(num =>  console.log(num)







ФИЛЬТР ПО СТРОКЕ

const tech = [
    {label: "HTML"},
    {label: "CSS"},
    {label: "JavaScript"},
    {label: "React"},
    {label: "Redux"},
    {label: "Node.js"},
    {label: "Vue"},
    {label: "MongoDB"},
    {label: "Mobx"},
];

const listEl = document.querySelector('.js-list');

const inputEl = document.querySelector(['#filter']);
inputEl.addEventListener('input', onFilterChange);

function renderAllList(tech) {
       return tech.map(val => `<li>${val.label}</li>`).join('');
    };
    
const labelValue = renderAllList(tech);

listEl.innerHTML = labelValue;

function onFilterChange (e) {
    const filter = e.target.value.toLowerCase();

    const filteredItem = tech.filter(v => 
        v.label.toLowerCase().includes(filter));

    const listItemsMarcup = renderAllList(filteredItem);

    listEl.innerHTML = listItemsMarcup;
};

EXPORT, IMPORT 
1. export default function() {}               import qwe from ‘./путь’

2. functionQ() {}
   functionA() {}

export default{functionQ, functionA}          import qwe from ‘./путь’

3.export functionQ() {}
  export functionA() {}                       import {Q, A} from ‘./путь’

4.export functionQ() {}
  export functionA() {}                       import * as qwe from ‘./путь’





JSON
JSON.stringify(obj) – приводит обьект или массив к строке.
JSON.parse(string) – возвращает оьбект или массив.

Local Storage
localStorage.setItem(‘key’,  ‘string’); - записать в локал сторедж только в виде строки
localStorage.getItem('key') — прочитать из локалсторедж;
localStorage.removeItem('textarea')- очистка локал сторедж;

setTimeout, setInterval
setTimeout(callback, 3000);                           setInterval(callback, 3000);
function callback() {                                  function callback() {
 console.log('Hello!')};                                console.log('Hello!')};                  вызыват один раз                                    вызыват через 3000мс постоянно

clearTimeout(id);-очищает                          clearInterval(id);-очищает

Promise
const promis = new Promise((resolve, reject) => {
const canFullfill = Math.random() > 0.5;

if (canFullfill) {
    resolve('Успех!');};

reject('Операция отклонена');});

promis.then(
    result => console.log(result)
            catch(
    error => console.log(error));
Перебор колекции Promises
const x = arr.map(data => data(Promise));
Promise.race, Promise.all
Promise.race(arr) – для ожидания самого бістрого промиса.
Promise.all(arr) – для ожидания всех промисов.

REST API
Запрос на сервер GET
fetch('https://pokeapi.co/api/v2/pokemon/2/')
.then(r => r.json())        - распарсит json
.then(r => console.log(r))  – при позитивном ответе
.catch(e => console.log(e)) – при ошибке
.finally(() => {})          - обрабатывается в любом случае






POSTMAN / CRUD
CREATE(POST) - postman: headers – Content-type, application/json. Body – raw, json.
const newBook = {
    "title": "Flay",
    "author": "Kolja",
    "genres": ["farr"],};

   function addBook(book) {
     const options = {
      method: 'POST',
      headers: {
        'Content-Type': 'application/json',
      },
      body: JSON.stringify(book),};

  return fetch(`${BASE_URL}/books`, options)
  .then(r => r.json())
  .then(console.log) };

  addBook(newBook);

READ(GET) – только правильный путь; Если один екземпляр, тогда по ID.

UPDATE(PATCH) – все как CREATE + передаем id(в конце пути /id) и что изменить в тело;
const options = {
      method: 'PATCH',
      headers: {
        'Content-Type': 'application/json',
      },
      body: JSON.stringify(book),};

DELETE(DELETE) - только правильный путь; Если один екземпляр, тогда по ID.
const options = {
      method: 'DELETE'}




1.создать файл .gitignore
  добавить node_modules/

2.создать файл .prettierrc.json

3. npm init -y

4. Установка Parcel
   npm install parcel-bundler --save-dev

5. Добавить два скрипта
"dev": "parcel <your entry file>",
    "build": "parcel build <your entry file>"

6. Создай два файла  index.html и index.js.

7. В файл index.html подключи скрипт
  <script src="./index.js"></script>

8. В скрипте парсела указываем точку входа. В данном примере
 это путь к index.html





 Деплой на гитхаб
1. npm run build 

2. В package.json добавляем свойство 
  "homepage": "https://myusername.github.io/my-app",
   выше перед зависимостями.
   Копируем имя на гитхабе и имя репозитория.

3. npm run build 

4. npm install --save gh-pages

5. Добавляем в скрипты
   "predeploy": "npm run build",
    "deploy": "gh-pages -d build"

6. npm run deploy


Деплой на NetliFY
1. В корне проекта создаем файл netlify.toml
  с настройками
[build]
publish = "build"

[[redirects]]
from = "/*"
to = "index.html"
status = 200

2. npm install netlify-cli -g

3. netlify login

4. Скрипты
"predeploy": "npm run build",
    "deploy": "netlify deploy -p"

5. npm run deploy

6. клавишей вниз выбираем создать и настроять новый проект

7. команду разработчиков оставляем

8. Придумываем уникальное имя