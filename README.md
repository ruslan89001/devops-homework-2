# Домашняя работа №2 — Ansible Playbook

## Задание

- Создать пользователя на удалённой машине
- Дать пользователю права sudo
- Настроить авторизацию SSH по ключам
- Отключить авторизацию по паролю при SSH подключении
- Создать директорию в `/opt/` с правами `660` для пользователя

---

## Окружение

| Параметр | Значение |
|---|---|
| Хостовая система | CachyOS (Arch Linux) |
| Гостевая система | Ubuntu 26.04 LTS (KVM/QEMU, virt-manager) |
| Сеть | libvirt NAT, `192.168.122.0/24` |
| IP гостевой VM | `192.168.122.50` |
| Управляемый пользователь | `devops` |

---

## Запуск

Скопировать публичный SSH ключ на управляемый хост:

```bash
ssh-copy-id -i ~/.ssh/id_ed25519.pub ruslan@192.168.122.50
```

Запустить playbook:

```bash
ansible-playbook -i inventory.ini playbook.yml
```

---

## Результат

![check1](screenshots/check1.jpeg)

**check1** — вывод `ansible-playbook` и проверка `ansible -i inventory.ini managed -m ping`

![check2](screenshots/check2.jpeg)

**check2** — подключение по SSH под `devops`, проверка `sudo whoami`, прав `/opt/devops_workdir` и `sshd_config`


