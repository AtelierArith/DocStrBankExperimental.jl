ラジオボタンのグループ - ユーザーは `options` の中から1つを選択できます。`options` は `String` の配列でも構いません。

`options` は `key::String => value::Any` のペアの配列でも構成できます。`key` は `@bind` を介して返され、`value` が表示されます。

# 例

`@bind veg Radio(["potato", "carrot"])`

`@bind veg Radio(["potato" => "🥔", "carrot" => "🥕"])`

`@bind veg Radio(["potato" => "🥔", "carrot" => "🥕"], default="carrot")`
