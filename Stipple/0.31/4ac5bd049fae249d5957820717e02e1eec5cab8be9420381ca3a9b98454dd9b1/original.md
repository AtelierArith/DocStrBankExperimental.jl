```
function init(::Type{M};
                vue_app_name::S = Stipple.Elements.root(M),
                endpoint::S = vue_app_name,
                channel::Union{Any,Nothing} = nothing,
                debounce::Int = JS_DEBOUNCE_TIME,
                throttle::Int = JS_THROTTLE_TIME,
                transport::Module = Genie.WebChannels,
                core_theme::Bool = true)::M where {M<:ReactiveModel, S<:AbstractString}
```

Initializes the reactivity of the model `M` by setting up the custom JavaScript for integrating with the Vue.js frontend and perform the 2-way backend-frontend data sync. Returns the instance of the model.

### Example

```julia
hs_model = Stipple.init(HelloPie)
```
