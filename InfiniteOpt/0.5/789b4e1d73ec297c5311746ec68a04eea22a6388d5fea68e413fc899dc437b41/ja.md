```
build_optimizer_model!(model::InfiniteModel; [kwargs...])
```

`model`に格納された最適化モデルを構築し、通常のJuMPモデルとして扱えるようにします。具体的には、`model`に格納された変数と制約を、最適化モデルに格納され、解決可能なものに変換します。これは、[`optimizer_model_key`](@ref)に従ってカスタム最適化モデルタイプを使用する拡張機能を考慮して一般的に提供されます。ただし、ユーザーが`optimize!`を呼び出さずにビルドを強制したい場合に特定のアプリケーションで役立つことがあります。拡張機能は、`build_optimizer_model!(model::InfiniteModel, key::Val{ext_key_name}; kwargs...)`の独自のバージョンを実装する必要があります。

**例**

```julia-repl
julia> build_optimizer_model!(model)

julia> optimizer_model_ready(model)
true
```
