```
objective(core::ExaCore, generator)
```

`generator`で指定された目的項を`core`に追加し、`Objective`オブジェクトを返します。注意: 項は合計されると仮定されています。

## 例

```jldoctest
julia> using ExaModels

julia> c = ExaCore();

julia> x = variable(c, 10);

julia> objective(c, x[i]^2 for i=1:10)
Objective

  min (...) + ∑_{p ∈ P} f(x,p)

  where |P| = 10
```
