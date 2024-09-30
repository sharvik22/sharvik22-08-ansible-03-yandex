# Домашнее задание к занятию 3 «Использование Ansible» Шарапат Виктор

## Подготовка к выполнению

1. Подготовьте в Yandex Cloud три хоста: для `clickhouse`, для `vector` и для `lighthouse`.
2. Репозиторий LightHouse находится [по ссылке](https://github.com/VKCOM/lighthouse).

## Основная часть

1. Допишите playbook: нужно сделать ещё один play, который устанавливает и настраивает LightHouse.
2. При создании tasks рекомендую использовать модули: `get_url`, `template`, `yum`, `apt`.
3. Tasks должны: скачать статику LightHouse, установить Nginx или любой другой веб-сервер, настроить его конфиг для открытия LightHouse, запустить веб-сервер.
4. Подготовьте свой inventory-файл `prod.yml`.
5. Запустите `ansible-lint site.yml` и исправьте ошибки, если они есть.
6. Попробуйте запустить playbook на этом окружении с флагом `--check`.
7. Запустите playbook на `prod.yml` окружении с флагом `--diff`. Убедитесь, что изменения на системе произведены.
8. Повторно запустите playbook с флагом `--diff` и убедитесь, что playbook идемпотентен.
9. Подготовьте README.md-файл по своему playbook. В нём должно быть описано: что делает playbook, какие у него есть параметры и теги.
10. Готовый playbook выложите в свой репозиторий, поставьте тег `08-ansible-03-yandex` на фиксирующий коммит, в ответ предоставьте ссылку на него.

---

### Решение

Данный плейбук устанавливает clickhouse, vector и lighthouse на 3 ВМ в yandex cloud.

Структура плейбука:

* group_vars - описываются переменные для приложений.
* inventory - описание групп хостовый машин, на которых будет выполняться плейбук.
* templates - шаблоны и конфиги для приложений.
* gitignore - файл исключения.
* site.yml - собстенно сам плейбук.

### Преподготовка

![Screenshot_3](https://github.com/user-attachments/assets/e9789520-164d-41f2-81ea-5fe97ae04cb6)

### Проверка на синтаксис плейбука

![5](https://github.com/user-attachments/assets/47b50c58-f074-4f61-8a17-bbfa3d5c8e1f)

### ansible-playbook -i inventory/prod.yml site.yml --ask-vault-pass

![6](https://github.com/user-attachments/assets/e7f884f2-f70d-4807-9ae5-e8e0355a581e)


### ansible-playbook -i inventory/prod.yml site.yml --ask-vault-pass --check

![7](https://github.com/user-attachments/assets/1337377d-3a05-4623-a1c8-0a386545d5da)

### ansible-playbook -i inventory/prod.yml site.yml --ask-vault-pass --diff

![8](https://github.com/user-attachments/assets/32546a85-ca7a-4090-82e4-8e6dac797ece)

### Дополнительные проверки на хостовый машинах

![Screenshot_1](https://github.com/user-attachments/assets/031fd8f3-64e6-4c5a-8fee-39ae1500710c)

![Screenshot_4](https://github.com/user-attachments/assets/b3059ebf-1a07-4947-b323-8efeb30a23d7)

![Screenshot_2](https://github.com/user-attachments/assets/57551a93-baf5-48e8-9d1f-d90b26dda307)

![Screenshot_5](https://github.com/user-attachments/assets/41bc477b-baa9-4af7-bad7-2993a4e4252a)

![Screenshot_6](https://github.com/user-attachments/assets/c79787e9-8d3c-447d-be31-30082ddf0fe0)
