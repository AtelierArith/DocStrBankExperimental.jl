```
set_optimizer_model(inf_model::InfiniteModel, opt_model::JuMP.Model;
                    inherit_optimizer::Bool = true)
```

`inf_model`を解決するために使用されるJuMPモデルを指定します。これは内部使用および拡張を目的としています。`opt_model`は、`inf_model`に対して[`TranscriptionModel`](@ref)に似た方法でマッピングできる拡張データを含む必要があります。`inherit_optimizer`は、新しい最適化モードで[`add_infinite_model_optimizer`](@ref)を呼び出すべきかどうかを示し、現在`inf_model`に保存されている最適化子のコンストラクタと属性を継承します。

**例**

```julia-repl
julia> set_optimizer_model(model, TranscriptionModel())

julia> optimizer_model(model)
A JuMP Model
Feasibility problem with:
Variables: 0
Model mode: AUTOMATIC
CachingOptimizer state: NO_OPTIMIZER
Solver name: No optimizer attached.
```
