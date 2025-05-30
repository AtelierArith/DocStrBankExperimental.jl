チェックボックスのグループ（`<input type="checkbox">`） - ユーザーは`options`の有効または無効を選択できます。`options`は`Strings`の配列です。`@bind`を介して返される値は、現在チェックされている項目を含むリストです。

参照: [`MultiSelect`](@ref)。

`options`は、ペアの配列`key::String => value::Any`でも構いません。`key`は`@bind`を介して返され、`value`が表示されます。

`defaults`は、初期状態でチェックされるべきオプションを指定します。

`orientation`は、オプションが`:row`または`:column`のどちらに配置されるべきかを指定します。

`select_all`は、「すべて選択」チェックボックスを含めるかどうかを指定します。

# 例

`@bind snacks MultiCheckBox(["🥕", "🐟", "🍌"]))`

`@bind snacks MultiCheckBox(["🥕" => "🐰", "🐟" => "🐱", "🍌" => "🐵"]; default=["🥕", "🍌"])`

`@bind animals MultiCheckBox(["🐰", "🐱" , "🐵", "🐘", "🦝", "🐿️" , "🐝",  "🐪"]; orientation=:column, select_all=true)`
