```
spectral_moments(order::Vector{Int}, m::S, r_ps::T, fas::FourierParameters, sdof::Oscillator; glxi::Vector{Float64}=xn31i, glwi::Vector{Float64}=wn31i, nodes::Int=length(glxi), control_freqs::Vector{Float64}=[1e-3, 1e-1, 1.0, 10.0, 100.0, 300.0] ) where {S<:Real,T<:Real}
```

指定された `order` のスペクトルモーメントのベクトルを計算します。

次の式を評価します：

$$
	m_k = 2\int_{0}^{\infty} \left(2\pi f\right)^k |H(f;f_n,\zeta_n)|^2 |A(f)|^2 df
$$

各オーダーについて、ここで $k$ はモーメントのオーダーです。

積分は、`nodes` ノードと重みを使用してガウス・ルジャンドル積分を使用して行われます。積分領域は、`control_freqs` の上に分割され、`sdof` 共鳴周波数の周りの積分の良好な近似を確保するために、`f_n/1.5` および `f_n*1.5` の2つの挿入周波数も含まれます。

参照： [`spectral_moment`](@ref), [`spectral_moments_gk`](@ref)
