```
sparse_init([::AbstractRNG=Utils.default_rng()], [T=Float32], dims::Integer...;
    sparsity::Number, std::Number=0.01) -> AbstractArray{T}
```

指定されたゼロ要素の割合で疎に初期化された重み行列を作成します。非ゼロ要素には正規分布から引き出されたランダムな数値が使用されます。このメソッドは[1]で導入されました。

!!! note
    sparsityパラメータは、ゼロに設定される行列の割合を制御します。たとえば、sparsityが0.3の場合、約30%の要素がゼロに設定されます。非ゼロ要素は、stdパラメータによってスケーリングされた正規分布に従って分布します。


# 引数

  * `rng::AbstractRNG`: 使用する乱数生成器。
  * `T::Type{<:Number}`: 戻り値の配列の要素の数値型。
  * `dims::Integer...`: 生成される重み行列の次元。
  * `sparsity::Number`: ゼロに設定される要素の割合。0と1の間でなければなりません。
  * `std::Number=0.01`: `gain`を適用する前の正規分布の標準偏差。

# 戻り値

  * `AbstractArray{T}`: 次元`dims`および型`T`の疎に初期化された重み行列。

# 例

```jldoctest
julia> y = sparse_init(Xoshiro(123), Float32, 5, 5; sparsity=0.3, std=0.01);

julia> y isa Matrix{Float32}
true

julia> size(y) == (5, 5)
true
```

# 参考文献

[1] Martens, J, "Deep learning via Hessian-free optimization" Proceedings of the 27th International Conference on International Conference on Machine Learning. 2010.
