```
params(m::MLJType)
```

透明なオブジェクト `m` を再帰的に、`m` のフィールドに基づいて名前付きタプルに変換します。オブジェクトは *透明* である場合、`MLJModelInterface.istransparent(m) == true` です。名前付きタプルは、`params` がフィールド値に再帰的に適用されるため、ネストされている可能性があります。フィールド値自体も透明である可能性があります。

`MLJType` 型のほとんどのオブジェクトは透明です。

```julia-repl
julia> params(EnsembleModel(model=ConstantClassifier()))
(model = (target_type = Bool,),
 weights = Float64[],
 bagging_fraction = 0.8,
 rng_seed = 0,
 n = 100,
 parallel = true,)
```
