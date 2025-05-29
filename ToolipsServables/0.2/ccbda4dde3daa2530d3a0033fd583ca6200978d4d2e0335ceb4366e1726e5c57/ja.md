#### toolips servables - コンポーザブルで多用途なパラメトリックコンポーネント

  * 0.3 1月
  * 2022年2月に [chifi](https://github.com/orgs/ChifiSource) によって作成されました
  * このソフトウェアはMITライセンスです。

`ToolipsServables` は、UIのテンプレート作成のためのコンポーザブルなパラメトリックプラットフォームを提供します。

```example
using ToolipsServables
# (From Toolips ?):
#using Toolips.Components

# コンポーネントの作成:
maindiv::Component{:div} = div("centered", align = "center")
greeter_heading::Component{:h3} = h3("greeter", text = "hello world!")
# スタイルの作成
bgstyle::Style = style("greeter_style", "color" => "white", 
"font-weight" => "bold")

# コンポーネントを直接スタイリング:
style!(maindiv, "background-color" => "purple", "margin-top" => 5px)
leavebutton = button("leave", text = "leave")
gobutton = button("go", text = "go!")

style!(gobutton, leavebutton)

# スタイルの作成
post_style = style("div.postbox", "border-radius" => 5px, "border" => "5px solid black")
fadein = keyframes("fadein")
                #  vv (または 0percent)
keyframes!(fadein, from, "opacity" => 0percent)
                #  vv (または 100percent)
keyframes!(fadein, to, "opacity" => 100percent)
style!(post_style, fadein)
# ボディの構成:
mainbod = body("mainbody")
    # アニメーション
style!(mainbod, fadein)
    # インラインスタイル
style!(mainbod, "padding" => 10percent, "background-color" => "lightblue")
    # ポストdivの生成
posts = ["hello world!", "post example"]
for (e, post) in enumerate(posts)
    comp = div("post$(e)")
    style!(comp, post_style)
    posthead = h4("head$(e)", text = "$(e)")
    postbody = p("body$(e)", text = post)
    style!(postbody, "font-size" => 13pt, "color" => "darkgray")
    push!(comp, posthead, postbody)
    # ボディにpush!:
    push!(mainbod, comp)
end
# コンポーネントは `write!` で書き込むことも、`String` に変換することもできます
# <:IO, <:Toolips.AbstractConnection, `String`
@info string(mainbod)
result = write!("", post_style, fadein, mainbod)
```

###### servable base

  * 抽象型 `Servable` end
  * `File` <: `Servable`
  * `AbstractComponent` <: `Servable`
  * `Component{T <: Any}` <: `AbstractComponent`
  * 抽象型 `StyleComponent` <: `AbstractComponent`
  * `Servables` (型エイリアス `Vector{<:Servable}`)
  * `write!(::IO, ::Servable)`
  * `write!(::String, ::Servable)`
  * `copy(c::Component{<:Any})`
  * `Style` <: `StyleComponentComponent`
  * 抽象型 `AbstractAnimation` <: `StyleComponent`
  * `KeyFrames` <: `AbstractAnimation`

###### テンプレーティング

`?(templating)` を使用して、ToolipsによるHTMLテンプレーティングについて詳しく学びます。

  * `img`
  * `link`
  * `meta`
  * `input`
  * `a`
  * `p`
  * `ul`
  * `li`
  * `br`
  * `i`
  * `title`
  * `span`
  * `iframe`
  * `svg`
  * `h1`
  * `h2`
  * `h3`
  * `h4`
  * `h5`
  * `h6`
  * `h`
  * `element`
  * `label`
  * `script`
  * `nav`
  * `button`
  * `form`
  * `section`
  * `body`
  * `header`
  * `footer`
  * `b`
  * `source`
  * `audio`
  * `video`
  * `table`
  * `tr`
  * `th`
  * `td`
  * `tmd`
  * `base64img`
  * `keyframes`
  * `style!`
  * `push!`
  * `textdiv`
  * `textbox`
  * `password`
  * `numberinput`
  * `rangeslider`
  * `option`
  * `options`
  * `select`
  * `checkbox`
  * `colorinput`
  * `progress`
  * `cursor`
  * `context_menu!`
  * `keyinput`
  * `textdiv_caret_tracker!`
  * `WebMeasure{format <: Any}`
  * `measures` (`?measures`)
  * `px`
  * `pt`
  * `inch`
  * `pc`
  * `mm`
  * `cm`
  * `percent`
  * `per`
  * `em`
  * `seconds`
  * `s`
  * `ms`
  * `deg`
  * `turn`
  * `rgba(r::Number, g::Number, b::Number, a::Float64)`
  * `from`
  * `to`
  * `translateX(s::String)`
  * `translateY(s::String)`
  * `rotate(s::String)`
  * `matrix(n::Int64 ...)`
  * `translate(x::String, y::String)`
  * `skew(one::String, two::String)`
  * `scale(n::Any)`
  * `scale(n::Any, n2::Any)`
  * **io**
  * `htmlcomponent`
  * `componenthtml`
  * `md_string`
  * `componentmd`
  * `interpolate`
  * `interpolate!`
