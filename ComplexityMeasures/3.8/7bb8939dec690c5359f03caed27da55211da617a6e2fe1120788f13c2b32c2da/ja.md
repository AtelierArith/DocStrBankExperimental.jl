```
BubbleSortSwapsEncoding <: Encoding
BubbleSortSwapsEncoding{m}()
```

`BubbleSortSwapsEncoding` は [`encode`](@ref) と共に使用され、長さ `m` の入力ベクトル `x` を整数にエンコードします。この整数は範囲 `ω ∈ 0:((m*(m-1)) ÷ 2)` にあり、バブルソートアルゴリズムが `x` を昇順にソートするために必要なスワップの数をカウントします。

[`decode`](@ref) はこのエンコーディングには実装されていません。

## 例

```julia
using ComplexityMeasures
x = [1, 5, 3, 1, 2]
e = BubbleSortSwapsEncoding{5}() # コンストラクタの型引数はベクトルの長さと一致する必要があります
encode(e, x)
```
