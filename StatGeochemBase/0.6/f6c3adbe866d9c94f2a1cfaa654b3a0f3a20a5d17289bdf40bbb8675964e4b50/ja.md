```julia
yq = linterp1(x::AbstractArray, y::AbstractArray, xq; extrapolate=:Linear)
```

1次元の単純な線形補間。ノットのベクトル `x` と値 `y` が与えられたとき、位置 `xq` に対応する `y` 値を見つけます。

ノット `x` は昇順にソートされている必要があります。

オプションのキーワード引数 `extrapolate` が `:Linear`（デフォルト）に設定されている場合、`x` の範囲外の `xq` 値は、最も近い2つの `x`-`y` ペアの線形外挿を使用して外挿されます。そうでない場合、`extrapolate` が `Number`（例：`0` または `NaN`）に設定されていると、その数値が代わりに使用されます。

### 例

```julia
julia> linterp1(1:10, 1:10, 5.5)
5.5

julia> linterp1(1:10, 1:10, 0.5:10.5)
11-element Vector{Float64}:
  0.5
  1.5
  2.5
  3.5
  4.5
  5.5
  6.5
  7.5
  8.5
  9.5
 10.5
```
