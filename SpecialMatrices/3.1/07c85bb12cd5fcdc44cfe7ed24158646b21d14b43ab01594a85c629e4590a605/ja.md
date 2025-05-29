```
Vandermonde(c::AbstractVector)
```

「遅延」`n × n` [`Vandermonde` 行列](https://en.wikipedia.org/wiki/Vandermonde_matrix)を作成します。ここで、$A_{ij} = c_i^{j-1}$であり、ベクトル`c`には`O(n)`のストレージのみを必要とします。

`transpose`および`adjoint`操作も遅延です。

```jldoctest van
julia> a = 1:5; A = Vandermonde(a)
5×5 Vandermonde{Int64}:
 1  1   1    1    1
 1  2   4    8   16
 1  3   9   27   81
 1  4  16   64  256
 1  5  25  125  625

julia> A'
5×5 adjoint(::Vandermonde{Int64}) with eltype Int64:
 1   1   1    1    1
 1   2   3    4    5
 1   4   9   16   25
 1   8  27   64  125
 1  16  81  256  625
```

バックラッシュ演算子`\`は、Björck & Pereyra (1970)のアルゴリズムを使用して、`O(n^2)`の時間でVandermondeおよびadjoint Vandermondeシステムを解決するようにオーバーロードされています。https://doi.org/10.2307/2004623

```jldoctest van
julia> A \ a
5-element Vector{Float64}:
 0.0
 1.0
 0.0
 0.0
 0.0

julia> A' \ A[2,:]
5-element Vector{Float64}:
 0.0
 1.0
 0.0
 0.0
 0.0
```
