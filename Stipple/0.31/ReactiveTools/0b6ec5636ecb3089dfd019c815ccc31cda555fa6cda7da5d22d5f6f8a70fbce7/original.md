```julia
@page(url, view; model::Union{Module, Type{<:ReactiveModel}, ReactiveModel},
                layout::Union{Genie.Renderers.FilePath,<:AbstractString,ParsedHTMLString,Nothing,Function} = nothing
                debounce::Int = Stipple.JS_DEBOUNCE_TIME,
                throttle::Int = Stipple.JS_THROTTLE_TIME,
                core_theme::Bool = true,
                pre::Union{Function, Vector{<:Function}} = Function[],
                post::Union{Function, Vector{<:Function}} = Function[])
```

Registers a new page with source in `view` to be rendered at the route `url`.

**Usage**

```julia
@page("/", "view.html")

@page("/", ui; model = MyApp) # for specifying an explicit app
```

### Other Parameters

  * `debounce`: debounce time in ms
  * `throttle`: throttle time in ms
  * `core_theme`: whether to use the core theme
  * `pre`: pre-rendering functions, e.g. for authentication

    Function definition: `pre1() = println("pre1").

    Call: `@page("/", ui, pre = pre1)` or `@page("/", ui, pre = [pre1, pre2, ...])`

    If the result of the function is not `nothing`, the rendering will be stopped and the result will be returned.
  * `post`: post-rendering functions, e.g. for modification of initial values of the model

    Function definition:

    `@handler function post1();      println("post1");      x = new_x;      println("changed initial value of :x to new_x");  end`   Model variables are accessible and can be modified in the post-rendering functions. For more details see [`@handler`](@ref).   Note that you need a model handler `@onchange isready @push` or `@onchange isready @push x` to update the variables after the model is ready.
