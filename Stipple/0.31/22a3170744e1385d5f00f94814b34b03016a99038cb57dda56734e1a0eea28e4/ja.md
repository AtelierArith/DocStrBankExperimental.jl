```
function Stipple.render(app::M, fieldname::Union{Symbol,Nothing} = nothing)::Dict{Symbol,Any} where {M<:ReactiveModel}
```

Juliaの`ReactiveModel` `app`を対応するVue.js JavaScriptコードとしてレンダリングします。
