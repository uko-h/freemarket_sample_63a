# README

## usersテーブル
|Column|Type|Options|
|------|----|-------|
|nickname|string|null: false, index: true|
|email|string|null: false, unique: true|
|encrypted_password|string|null: false|
|family_name|string|null: false|
|last_name|string|null: false|
|family_name_kana|string|null: false|
|last_name_kana|string|null: false|
|birth_year|integer|null: false|
|birth_month|integer|null: false|
|birth_day|integer|null: false|

### Association
- has_many :destinations
- has_many :products
- has_many :credit_cards
- has_many :purchases


## destinationsテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|references|null: false, foreign_key: true|
|family_name|string|null: false|
|last_name|string|null: false|
|family_name_kana|string|null: false|
|last_name_kana|string|null: false|
|zip_code|integer|null: false|
|prefecture|string|null: false|
|municipality|string|null: false|
|address|string|null: false|
|apartment_name|string|
|phone_number|string|

### Association
- belongs_to :user


## productsテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|references|null: false, foreign_key: true|
|name|string|null: false|
|description|text|null: false|
|category_id|references|null: false, foreign_key: true|
|brand_id|references|null: false, foreign_key: true|
|condition|string|null: false|
|delivery_charge|string|null: false|
|delivery_origin|string|null: false|
|shipping_date|string|null: false|
|price|integer|null: false|

### Association
- belongs_to :user
- belongs_to :category
- belongs_to :brand
- has_many :images


## product_imagesテーブル
|Column|Type|Options|
|------|----|-------|
|product_id|references|null: false, foreign_key: true|
|image_1|string|null: false|
|image_2|string|
|image_3|string|
|image_4|string|
|image_5|string|
|image_6|string|
|image_7|string|
|image_8|string|
|image_9|string|
|image_10|string|

### Association
- belongs_to :product


## purchaseテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|references|null: false, foreign_key: true|
|product_id|integer|null: false|

### Association
- belongs_to :user


## categoriesテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false|
|ancestry|string|null: false|

### Association
- has_many :products
- has_ancestry


## brandsテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false|
|ancestry|string|null: false|

### Association
- has_many :products
- has_ancestry


## credit_cardsテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|references|null: false, foreign_key: true|
|customer_id|string|null: false|
|card_id|string|null: false|

### Association
- belongs_to :user