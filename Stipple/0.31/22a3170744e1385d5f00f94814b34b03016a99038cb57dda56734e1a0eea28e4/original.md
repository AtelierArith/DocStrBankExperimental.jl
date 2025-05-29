```
function Stipple.render(app::M, fieldname::Union{Symbol,Nothing} = nothing)::Dict{Symbol,Any} where {M<:ReactiveModel}
```

Renders the Julia `ReactiveModel` `app` as the corresponding Vue.js JavaScript code.
