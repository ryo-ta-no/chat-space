# README

This README would normally document whatever steps are necessary to get the
application up and running.

Things you may want to cover:

* Ruby version

* System dependencies

* Configuration

* Database creation

* Database initialization

* How to run the test suite

* Services (job queues, cache servers, search engines, etc.)

* Deployment instructions

* ...

## groupsテーブル

|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|

### Association
has_many :users, through: :groups_users
has_many :groups_users
has_many :messages

## messagesテーブル

|Column|Type|Option|
|------|----|------|
|body|text|null: false|
|image|string|
|group_id|integer|foreign_key: true|
|user_id|integer|foreign_key: true|

### Association
- belongs_to :group
- belongs_to :user

## usersテーブル

|Cloumn|Type|Option|
|------|----|------|
|name|string|index: true, null: false, unique: true|
|email|string|null: false, unipue: true|

### Associacion
- has_many :groups, through: :groups_users
- has_many :groups_users
- has_many :massages

## groups_users

|Cloumn|Type|Option|
|------|----|------|
|group|references|index: true, foreign_key: true, null: false|
|user|references|index: true, foreign_key: true, null: false|

### Associacion
- belongs_to :group
- belongs_to :user