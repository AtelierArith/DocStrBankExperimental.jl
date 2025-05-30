ドロップダウンメニュー（`<select>`） - ユーザーは`options`の中から1つを選択できます。`options`は`String`の配列です。

複数の選択項目を許可するバージョンについては、[`MultiSelect`](@ref)を参照してください。

`options`は、`key::Any => display_value::String`のペアの配列でも構いません。`key`は`@bind`を介して返され、`display_value`が表示されます。

# 例

`@bind veg Select(["potato", "carrot"])`

`@bind veg Select(["potato" => "🥔", "carrot" => "🥕"])`

`@bind veg Select(["potato" => "🥔", "carrot" => "🥕"], default="carrot")`

この3つのケースすべてで、`veg`は`"potato"`または`"carrot"`になります。

*key*は文字列、数値、または関数など、任意のオブジェクトにすることができます：

```julia
@bind f Select([cos => "cosine function", sin => "sine function"])

f(0.5)
```
