# mac_setup

## 1. Xcodeをインストール

https://developer.apple.com/download/more/#

## 2. Ansibleをpipでインストール

```
$ sudo easy_install pip
$ sudo pip install ansible
$ sudo pip install ansible --upgrade
```

## 3. Ansible.cfgを作成

```
$ sudo mkdir /etc/ansible
$ sudo curl -L https://raw.githubusercontent.com/ansible/ansible/devel/examples/ansible.cfg \
  -o /etc/ansible/ansible.cfg
```

## 4. Homebrewをインストール

```
$ /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

## 5. masterブランチをzipで落として解凍する

```
$ curl -LOk https://github.com/yastani/mac_setup/archive/master.zip
$ unzip -jd mac_setup master.zip
```

## 6. Ansible playbookを実行

```
$ cd $(find ~/ * 2> /dev/null | grep -e \s*mac_setup$)
$ cat << EOF > inventory
[localhost]
127.0.0.1
EOF
$ ansible-playbook main.yml -i inventory
```
