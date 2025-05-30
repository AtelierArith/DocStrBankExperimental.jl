```julia
constraint(
    model::CTModels.Model,
    label::Symbol
) -> Tuple{Symbol, Any, Any, Any}

```

モデルからラベル付き制約を取得します。返されるタプルは `(type, f, lb, ub)` の形式であり、`type` は制約のタイプ、`f` は制約の関数、`lb` は制約の下限、`ub` は制約の上限です。

ラベルがモデルに見つからない場合、関数は例外を返します。
