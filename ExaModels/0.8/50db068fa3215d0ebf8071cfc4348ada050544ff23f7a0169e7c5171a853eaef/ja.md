```
variable(core, dims...; start = 0, lvar = -Inf, uvar = Inf)
```

`dims`で指定された次元を持つ変数を`core`に追加し、`Variable`オブジェクトを返します。`dims`は`Integer`または`UnitRange`のいずれかです。

## キーワード引数

  * `start`: 解の初期推定値。`Number`、`AbstractArray`、または`Generator`のいずれかであることができます。
  * `lvar` : 変数の下限。`Number`、`AbstractArray`、または`Generator`のいずれかであることができます。
  * `uvar` : 変数の上限。`Number`、`AbstractArray`、または`Generator`のいずれかであることができます。

## 例

```jldoctest
julia> using ExaModels

julia> c = ExaCore();

julia> x = variable(c, 10; start = (sin(i) for i=1:10))
Variable

  x ∈ R^{10}

julia> y = variable(c, 2:10, 3:5; lvar = zeros(9,3), uvar = ones(9,3))
Variable

  x ∈ R^{9 × 3}

```
