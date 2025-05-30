ラジオボタンのグループ - ユーザーは `options` の中から1つを選択できます。`options` は `String` の配列でも、ペアの配列 `key::String => value::Any` でも構いません。`key` は `@bind` を介して返され、`value` が表示されます。

# 例

`@bind veg Radio(["potato", "carrot"])`

`@bind veg Radio(["potato" => "🥔", "carrot" => "🥕"])`

`@bind veg Radio(["potato" => "🥔", "carrot" => "🥕"], default="carrot")`
