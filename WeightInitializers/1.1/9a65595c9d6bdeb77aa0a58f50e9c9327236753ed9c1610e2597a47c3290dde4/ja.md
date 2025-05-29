```
orthogonal([::AbstractRNG=Utils.default_rng()], [T=Float32], dims::Integer...;
    gain = 1)  -> AbstractArray{T, length(dims)}
```

与えられた次元（`dims`）の `AbstractArray{T}` を返します。これは（半）直交行列であり、[1] に記載されています。

この関数は、指定された次元に応じて直交行列または半直交行列を構築します。2次元の場合、`dims = (rows, cols)` の行列を返します。2次元以上の場合、`prod(dims[1:(end - 1)])` サイズの直交行列を `dims[end]` に対して計算し、元の次元に再整形します。

ベクトルを構築することはできません。すなわち、`length(dims) == 1` は禁止されています。

# 引数

  * `rng::AbstractRNG`: 擬似乱数生成器。
  * `T::Type{<:Real}`: 配列の要素の型。
  * `dims::Integer...`: 配列の次元。
  * `gain::Number`: 直交行列の要素のスケーリング係数。

# 参考文献

[1] Saxe, McClelland, Ganguli. "Exact solutions to the nonlinear dynamics of learning in deep linear neural networks", ICLR 2014, https://arxiv.org/abs/1312.6120 ```
