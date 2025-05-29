mri*smap*basis(mask ; kmax, kt, ki)

MRI感度マップを分離可能な複素指数信号の形で表現するためのフーリエ基底を構築します。形式は `basis = (k,N) -> exp.(2im * π * nfun(N) * kfun(k,N))` です。デフォルトは `nfun(N) = -(N÷2):(N÷2)-1` で、これは偶数の `N` のみ適しています。デフォルトは `kfun(k,N) = k / 2N` で、これはDCT-IIのような周波数であり、DFT周波数 `k/N` よりも境界の挙動が良好です。

# 入力

  * `mask::AbstractArray{Bool,D}` 再構築する領域のバイナリサポートマスク

# オプション

  * `kmax::Int = 5` デフォルトの周波数インデックス -kmax:kmax のすべての次元
  * `kfun::Function = (k,N) -> k / (2N)` # DCT-II周波数
  * `deltas::NTuple{D,<:Number} = ones(D)` ピクセルサイズ

（追加のオプション `kmaxs`、`kt`、`ki`、`T` については、コードを参照してください。）

# 出力

  * `(; B, ν)` ここで `B` はサイズ `count(mask) × nk` の基底行列であり、通常 `nk = (2*kmax+1)^D` です。また `ν` は `nk` 周波数タプルであり、各タプルは `ν = kfun.(Tuple(k), size(mask)) ./ deltas` の形を持ちます。
