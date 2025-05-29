#### toolips servables - composable and versatile parametric components

  * 0.3 January
  * Created in February, 2022 by [chifi](https://github.com/orgs/ChifiSource)
  * This software is MIT-licensed.

`ToolipsServables` provides a composable parametric platform for templating      UIs.

```example
using ToolipsServables
# (From Toolips ?):
#using Toolips.Components

# creating components:
maindiv::Component{:div} = div("centered", align = "center")
greeter_heading::Component{:h3} = h3("greeter", text = "hello world!")
# creating a style
bgstyle::Style = style("greeter_style", "color" => "white", 
"font-weight" => "bold")

# styling a component directly:
style!(maindiv, "background-color" => "purple", "margin-top" => 5px)
leavebutton = button("leave", text = "leave")
gobutton = button("go", text = "go!")

style!(gobutton, leavebutton)

# creting styles
post_style = style("div.postbox", "border-radius" => 5px, "border" => "5px solid black")
fadein = keyframes("fadein")
                #  vv (or 0percent)
keyframes!(fadein, from, "opacity" => 0percent)
                #  vv (or 100percent)
keyframes!(fadein, to, "opacity" => 100percent)
style!(post_style, fadein)
# composing a body:
mainbod = body("mainbody")
    # animation
style!(mainbod, fadein)
    # inline styles
style!(mainbod, "padding" => 10percent, "background-color" => "lightblue")
    # generating post divs
posts = ["hello world!", "post example"]
for (e, post) in enumerate(posts)
    comp = div("post$(e)")
    style!(comp, post_style)
    posthead = h4("head$(e)", text = "$(e)")
    postbody = p("body$(e)", text = post)
    style!(postbody, "font-size" => 13pt, "color" => "darkgray")
    push!(comp, posthead, postbody)
    # push! to body:
    push!(mainbod, comp)
end
# components can be written with `write!` or turned to a `String` with `string`
# <:IO, <:Toolips.AbstractConnection, `String`
@info string(mainbod)
result = write!("", post_style, fadein, mainbod)
```

###### servable base

  * abstract type `Servable` end
  * `File` <: `Servable`
  * `AbstractComponent` <: `Servable`
  * `Component{T <: Any}` <: `AbstractComponent`
  * abstract type `StyleComponent` <: `AbstractComponent`
  * `Servables` (type alias for `Vector{<:Servable}`)
  * `write!(::IO, ::Servable)`
  * `write!(::String, ::Servable)`
  * `copy(c::Component{<:Any})`
  * `Style` <: `StyleComponentComponent`
  * abstract type `AbstractAnimation` <: `StyleComponent`
  * `KeyFrames` <: `AbstractAnimation`

###### templating

use `?(templating)` to learn more about HTML templating with Toolips.

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
