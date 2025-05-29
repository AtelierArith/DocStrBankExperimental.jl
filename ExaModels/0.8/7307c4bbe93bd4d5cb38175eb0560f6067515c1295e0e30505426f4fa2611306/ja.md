```
constraint(core, generator; start = 0, lcon = 0,  ucon = 0)
```

`core`に`generator`によって指定された制約を追加し、`Constraint`オブジェクトを返します。

## キーワード引数

  * `start`: 解の初期推定値。`Number`、`AbstractArray`、または`Generator`のいずれかである必要があります。
  * `lcon` : 制約の下限。`Number`、`AbstractArray`、または`Generator`のいずれかである必要があります。
  * `ucon` : 制約の上限。`Number`、`AbstractArray`、または`Generator`のいずれかである必要があります。

## 例

```jldoctest
julia> using ExaModels

julia> c = ExaCore();

julia> x = variable(c, 10);

julia> constraint(c, x[i] + x[i+1] for i=1:9; lcon = -1, ucon = (1+i for i=1:9))
Constraint

  s.t. (...)
       g♭ ≤ [g(x,p)]_{p ∈ P} ≤ g♯

  ここで |P| = 9
```
