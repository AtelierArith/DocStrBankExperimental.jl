```
hvp_and_gradient!(res::X, grad::X, f::F, x::X, v::X) where {F, X}
```

配列入力スカラー出力関数 `f` のインプレースヘッセ行列-ベクトル積を計算します。これは、`x` で評価された `f` にベクトル `v` を掛けたものと、勾配を計算し、勾配を `grad` に格納します。ヘッセ行列-ベクトル積と勾配は、別々に計算するよりも効率的に同時に計算できます。

結果は `res` に格納されます。勾配は `grad` に格納されます。

言い換えれば、`res .= hessian(f)(x) * v` と `grad .= gradient(Reverse, f)(x)` を計算します。

例:

```jldoctest hvp_and_gradient; filter = r"([0-9]+\.[0-9]{8})[0-9]+" => s"\1***"
f(x) = sin(x[1] * x[2])

res = Vector{Float64}(undef, 2)
grad = Vector{Float64}(undef, 2)
hvp_and_gradient!(res, grad, f, [2.0, 3.0], [5.0, 2.7])

res
grad
# output
2-element Vector{Float64}:
 2.880510859951098
 1.920340573300732
```
