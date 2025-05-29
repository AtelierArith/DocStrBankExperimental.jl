```julia
style!(::AbstractComponent, ...) -> ::Nothing
```

`style!` is used to mutate the style of components and style components  using CSS pairs, or in the case of components using a `Style` or `Animation`.  `style!` will take a component followed by what to style that component with.  This can be an infinite list of properties and values, the keys must be strings,  (`?style_properties`) or a `Style`/`Animation`.

```julia
# response-side style!
# style a `Component` directly:
style!(c::AbstractComponent, s::Pair{String, <:Any} ...)
# style a Component's child:
style!(c::Component{<:Any}, child::String, p::Pair{String, String} ...)
# set a `Component`'s class to a style's name.
style!(comp::Component{<:Any}, sty::Style)
# styles a style with the animation `anim`(be sure to write `anim`):
style!(sty::Style, anim::AbstractAnimation)
# styles a component with the animation `anim` (be sure to write `anim`):
style!(comp::Component{<:Any}, anim::AbstractAnimation)
```

  * See also: `keyframes`, `set_children!`, `style!`, `templating`, `measures`

```example
mycomp = div("mysample", text = "hello world!")
style!(mycomp, "display" => "inline-block", "background-color" => "black")

myclass = style("div.sample", "color" => "white")

style!(mycomp, myclass)
```
