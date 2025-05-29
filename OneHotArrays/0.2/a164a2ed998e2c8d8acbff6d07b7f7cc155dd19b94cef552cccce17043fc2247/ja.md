```
onehotbatch(xs, labels, [default])
```

[`OneHotMatrix`](@ref) を返します。ここで、行列の `k` 番目の列は [`onehot(xs[k], labels)`](@ref onehot) です。これはスパース行列で、非ゼロ要素のインデックスを含む `Vector{UInt32}` だけを格納します。

`xs` の入力のいずれかが `labels` に見つからない場合、その列は `default` が指定されている場合は `onehot(default, labels)` になり、指定されていない場合はエラーになります。

`xs` がより多くの次元を持つ場合、`N = ndims(xs) > 1` では、結果は `AbstractArray{Bool, N+1}` であり、最初の次元に沿ってワンホットになります。すなわち、`result[:, k...] == onehot(xs[k...], labels)` です。

`xs` は文字列などの任意のイテラブルであることに注意してください。また、`labels` にタプルを使用すると、特に32クラス未満の場合、構築が速くなることがよくあります。

# 例

```jldoctest
julia> oh = onehotbatch("abracadabra", 'a':'e', 'e')
5×11 OneHotMatrix(::Vector{UInt32}) with eltype Bool:
 1  ⋅  ⋅  1  ⋅  1  ⋅  1  ⋅  ⋅  1
 ⋅  1  ⋅  ⋅  ⋅  ⋅  ⋅  ⋅  1  ⋅  ⋅
 ⋅  ⋅  ⋅  ⋅  1  ⋅  ⋅  ⋅  ⋅  ⋅  ⋅
 ⋅  ⋅  ⋅  ⋅  ⋅  ⋅  1  ⋅  ⋅  ⋅  ⋅
 ⋅  ⋅  1  ⋅  ⋅  ⋅  ⋅  ⋅  ⋅  1  ⋅

julia> reshape(1:15, 3, 5) * oh  # この行列の乗算は効率的に行われます
3×11 Matrix{Int64}:
 1  4  13  1  7  1  10  1  4  13  1
 2  5  14  2  8  2  11  2  5  14  2
 3  6  15  3  9  3  12  3  6  15  3
```
