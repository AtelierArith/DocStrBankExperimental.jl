```
synalm!(cl::Vector{T}, alm::Alm{ComplexF64, Vector{ComplexF64}}, rng::AbstractRNG) where {T <: Real}
synalm!(cl::Vector{T}, alm::Alm{ComplexF64, Vector{ComplexF64}}) where {T <: Real}
```

与えられたパワースペクトル $C_{\ell}$ から $a_{\ell m}$ のセットを生成します。出力は入力として渡された `Alm` オブジェクトに書き込まれます。

# 引数:

  * `cl::AbstractVector{T}`: パワースペクトル成分 $C_{\ell}$ を表す配列で、$\ell = 0$ から始まります。
  * `alm::Alm{Complex{T}}`: 結果を書き込みたい球面調和係数 $a_{\ell m}$ を表す配列です。
  * `rng::AbstractRNG` : （オプション）$a_{\ell m}$ を生成するために使用されるRNGです。これにより、事前にシードを設定してプロセスの再現性を保証することができます。
