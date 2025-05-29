```julia
style!(::AbstractComponent, ...) -> ::Nothing
```

`style!` は、コンポーネントのスタイルを変更し、CSSペアを使用してコンポーネントのスタイルを設定するために使用されます。また、コンポーネントが `Style` または `Animation` を使用している場合にも適用されます。 `style!` は、コンポーネントとそのコンポーネントにスタイルを適用するための引数を取ります。これは無限のプロパティと値のリストであり、キーは文字列でなければなりません（`?style_properties`）または `Style`/`Animation` です。

```julia
# レスポンス側のスタイル!
# `Component` を直接スタイル設定する:
style!(c::AbstractComponent, s::Pair{String, <:Any} ...)
# コンポーネントの子をスタイル設定する:
style!(c::Component{<:Any}, child::String, p::Pair{String, String} ...)
# `Component` のクラスをスタイルの名前に設定する。
style!(comp::Component{<:Any}, sty::Style)
# スタイルをアニメーション `anim` でスタイル設定する（`anim` と書くことを忘れないでください）:
style!(sty::Style, anim::AbstractAnimation)
# コンポーネントをアニメーション `anim` でスタイル設定する（`anim` と書くことを忘れないでください）:
style!(comp::Component{<:Any}, anim::AbstractAnimation)
```

  * 参照: `keyframes`, `set_children!`, `style!`, `templating`, `measures`

```example
mycomp = div("mysample", text = "hello world!")
style!(mycomp, "display" => "inline-block", "background-color" => "black")

myclass = style("div.sample", "color" => "white")

style!(mycomp, myclass)
```
