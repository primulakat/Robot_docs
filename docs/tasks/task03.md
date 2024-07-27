# T-03 Оформление заказа

### Материалы к задаче

Use case: [UC-07 Оформление заказа](../requirements/uc07.md), [UC-08 Оплата заказа картой](../requirements/uc08.md)

Интерфейсы: [WF-05 Оформление заказа](../user_interface/wf05.md), [WF-06 Оплата заказа картой](../user_interface/wf06.md)

API методы: Оформление заказа, Оплата заказа картой

*Приложены: документация API платежной системы, маппинг данных*
### Тест-кейсы

#### **`TC-03.01`** Оформление заказа: в зале, как можно скорее, с оплатой банковской картой

Предусловия

1. Кассовый день открыт.
3. Приложение запущено, открыта корзина.
4. В корзину добавлено как минимум одно блюдо.

Постусловия

1. Заказ оформлен.
2. Номер заказа отображается на табло в зале и в карточке заказа.

| Шаг | Действие                                                       | Ожидаемый результат                                                                                                                                                                                                                                                                     |
| --- | -------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1   | Нажать кнопку «Оформить заказ»                                 | Отображается экран оформления заказа. Отображается список выбранных блюд.                                                                                                                                                                                                               |
| 2   | Выбрать способ получения заказа «В зале»                       | Пользователь видит выбранный способ получения заказа «В зале».                                                                                                                                                                                                                          |
| 3   | Выбрать время получения заказа «Как можно скорее»              | Пользователь видит выбранное время получения заказа «Как можно скорее».                                                                                                                                                                                                                 |
| 4   | Выбрать способ оплаты «Банковской картой»                      | Пользователь видит выбранный способ оплаты «Банковской картой».                                                                                                                                                                                                                         |
| 5   | Нажать кнопку «Оплатить заказ»                                 | Отображается ошибка: нужно указать персональные данные.                                                                                                                                                                                                                                 |
| 6   | Указать персональные данные: имя, телефон, электронная почта   | Пользователь видит указанные персональные данные: имя, телефон, электронная почта.                                                                                                                                                                                                      |
| 7   | Нажать кнопку «Оплатить заказ»                                 | Отображается форма оплаты заказа.                                                                                                                                                                                                                                                       |
| 8   | Не заполнять ни одно из полей: номер карты, месяц/год, CVV/CVC | Пользователь видит незаполненные поля формы.                                                                                                                                                                                                                                            |
| 9   | Нажать кнопку «Оплатить»                                       | У каждого из полей номер карты, месяц/год, CVV/CVC отображается сообщение о необходимости заполнить поле.                                                                                                                                                                               |
| 10  | В поле «номер карты» ввести буквы и спецсимволы                | Не удается ввести.                                                                                                                                                                                                                                                                      |
| 11  | В поле «месяц/год» ввести буквы и спецсимволы                  | Не удается ввести.                                                                                                                                                                                                                                                                      |
| 12  | В поле «CVV/CVC» ввести буквы и спецсимволы                    | Не удается ввести.                                                                                                                                                                                                                                                                      |
| 13  | В поле «номер карты» ввести более 16 цифр                      | Не удается ввести более 16 цифр.                                                                                                                                                                                                                                                        |
| 14  | В поле «месяц/год» ввести более 4 цифр                         | Не удается ввести более 4 цифр.                                                                                                                                                                                                                                                         |
| 15  | В поле «CVV/CVC» ввести более 3 цифр                           | Не удается ввести более 3 цифр.                                                                                                                                                                                                                                                         |
| 16  | В поле «номер карты» ввести менее 16 цифр                      | Пользователь видит частично заполненный номер карты.                                                                                                                                                                                                                                    |
| 17  | В поле «месяц/год» ввести менее 4 цифр                         | Пользователь видит частично заполненные месяц/год.                                                                                                                                                                                                                                      |
| 18  | В поле «CVV/CVC» ввести менее 3 цифр                           | Пользователь видит частично заполненный CVV/CVC.                                                                                                                                                                                                                                        |
| 19  | Нажать кнопку «Оплатить»                                       | У каждого из полей номер карты, месяц/год, CVV/CVC отображается сообщение о неверно введенных данных.                                                                                                                                                                                   |
| 20  | Верно ввести номер карты: 16 цифр от 0 до 9                    | Пользователь видит заполненный номер карты.                                                                                                                                                                                                                                             |
| 21  | Верно ввести месяц/год: 4 цифры от 0 до 9                      | Пользователь видит заполненные месяц/год.                                                                                                                                                                                                                                               |
| 22  | Верно ввести CVV/CVC: 3 цифры от 0 до 9                        | Пользователь видит заполненный CVV/CVC.                                                                                                                                                                                                                                                 |
| 23  | Нажать кнопку «Оплатить»                                       | Во время отправки запроса в банк отображается лоадер.<br>После успешной отработки запроса отображается карточка заказа с сообщением «Заказ успешно оформлен и передан на кухню». Указан номер заказа для получения.<br>Номер заказа отображается на табло в зале в колонке «Готовятся». |

#### **`TC-03.02`** Оформление заказа: навынос, ко времени, с оплатой наличными

Предусловия

1. Кассовый день открыт.
3. Приложение запущено, открыта корзина.
4. В корзину добавлено как минимум одно блюдо.

Постусловия

1. Заказ оформлен.
2. Номер заказа отображается на табло в зале и в карточке заказа.

| Шаг | Действие                                                     | Ожидаемый результат                                                                                                                                                                              |
| --- | ------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| 1   | Нажать кнопку «Оформить заказ»                               | Отображается экран оформления заказа. Отображается список выбранных блюд.                                                                                                                        |
| 2   | Выбрать способ получения заказа «Навынос»                    | Пользователь видит выбранный способ получения заказа «Навынос».                                                                                                                                  |
| 3   | Выбрать время получения заказа «Ко времени»                  | Пользователь видит выбранное время получения заказа «Ко времени» и поле для выбора времени готовности заказа.                                                                                    |
| 4   | Указать время готовности заказа                              | Пользователь видит указанное время готовности заказа.                                                                                                                                            |
| 5   | Выбрать способ оплаты «Наличными при получении»              | Пользователь видит выбранный способ оплаты «Наличными при получении».                                                                                                                            |
| 6   | Указать персональные данные: имя, телефон, электронная почта | Пользователь видит указанные персональные данные: имя, телефон, электронная почта.                                                                                                               |
| 7   | Нажать кнопку «Оформить заказ»                               | Отображается карточка заказа с сообщением «Заказ успешно оформлен и передан на кухню».<br>Указан номер заказа для получения.<br>Номер заказа отображается на табло в зале в колонке «Готовятся». |


#### **`TC-03.03`** Оформление заказа: одно или несколько блюд или ингредиентов недоступны

Предусловия

1. Кассовый день открыт.
3. Приложение запущено, открыта корзина.
4. В корзину добавлено как минимум одно блюдо.

Постусловия

1. Заказ оформлен.
2. Номер заказа отображается на табло в зале и в карточке заказа.

| Шаг | Действие                                                     | Ожидаемый результат                                                                                                                                                                                                                                                                     |
| --- | ------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1   | Нажать кнопку «Оформить заказ»                               | Отображается экран оформления заказа. Отображается список выбранных блюд.                                                                                                                                                                                                               |
| 2   | Выбрать способ получения заказа «В зале»                     | Пользователь видит выбранный способ получения заказа «В зале».                                                                                                                                                                                                                          |
| 3   | Выбрать время получения заказа «Как можно скорее»            | Пользователь видит выбранное время получения заказа «Как можно скорее».                                                                                                                                                                                                                 |
| 4   | Выбрать способ оплаты «Банковской картой»                    | Пользователь видит выбранный способ оплаты «Банковской картой».                                                                                                                                                                                                                         |
| 5   | Указать персональные данные: имя, телефон, электронная почта | Пользователь видит указанные персональные данные: имя, телефон, электронная почта.                                                                                                                                                                                                      |
| 6   | Нажать кнопку «Оплатить заказ»                               | Отображается уведомление, что часть блюд стали недоступны для заказа, и предложение сделать замену или удалить блюдо из заказа.                                                                                                                                                         |
| 7   | Выбрать «заменить блюдо»                                     | Отображает меню ресторана.                                                                                                                                                                                                                                                              |
| 8   | Выбрать блюдо для замены                                     | Выбранное блюдо отображается на экране оформления заказа.                                                                                                                                                                                                                               |
| 9   | Нажать кнопку «Оплатить заказ»                               | Отображается форма оплаты заказа.                                                                                                                                                                                                                                                       |
| 10  | Верно ввести номер карты: 16 цифр от 0 до 9                  | Пользователь видит заполненный номер карты                                                                                                                                                                                                                                              |
| 11  | Верно ввести месяц/год: 4 цифры от 0 до 9                    | Пользователь видит заполненные месяц/год                                                                                                                                                                                                                                                |
| 12  | Верно ввести CVV/CVC: 3 цифры от 0 до 9                      | Пользователь видит заполненный CVV/CVC                                                                                                                                                                                                                                                  |
| 13  | Нажать кнопку «Оплатить»                                     | Во время отправки запроса в банк отображается лоадер.<br>После успешной отработки запроса отображается карточка заказа с сообщением «Заказ успешно оформлен и передан на кухню». Указан номер заказа для получения.<br>Номер заказа отображается на табло в зале в колонке «Готовятся». |