マルチセレクタ（`<select multi>`） - ユーザーは `options` の中から1つ以上を選択できます。`options` は `Strings` の配列です。

単一の選択項目のみを許可するバージョンについては [`Select`](@ref) を参照してください。

`options` は `key::String => value::Any` のペアの配列でも構いません。`key` は `@bind` を介して返され、`value` が表示されます。

`size` キーワード引数を使用して、一度に表示される行数を指定できます。

[`select`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/select) に関する Mozilla のドキュメントを参照してください。

# 例

`@bind veg MultiSelect(["potato", "carrot"])`

`@bind veg MultiSelect(["potato" => "🥔", "carrot" => "🥕"])`

`@bind veg MultiSelect(["potato" => "🥔", "carrot" => "🥕"], default=["carrot"])`

`@bind letters MultiSelect(string.('a':'z'), size=20)`
