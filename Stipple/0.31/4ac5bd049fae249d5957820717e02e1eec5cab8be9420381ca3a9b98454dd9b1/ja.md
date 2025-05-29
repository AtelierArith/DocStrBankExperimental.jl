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

モデル `M` のリアクティビティを初期化し、Vue.js フロントエンドとの統合のためのカスタム JavaScript を設定し、バックエンドとフロントエンドのデータ同期を双方向で行います。モデルのインスタンスを返します。

### 例

```julia
hs_model = Stipple.init(HelloPie)
```
