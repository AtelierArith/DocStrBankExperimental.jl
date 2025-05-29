```
spectral_moment(order::Int, m::S, r_ps::T, fas::FourierParameters, sdof::Oscillator; nodes::Int=31, control_freqs::Vector{Float64}=[1e-3, 1e-1, 1.0, 10.0, 100.0, 300.0] ) where {S<:Real,T<:Real}
```

指定された次数のスペクトルモーメントを計算します。

次の式を評価します：

$$
	m_k = 2\int_{0}^{\infty} \left(2\pi f\right)^k |H(f;f_n,\zeta_n)|^2 |A(f)|^2 df
$$

ここで、$k$はモーメントの次数です。

積分は、`nodes`ノードと重みを使用してガウス・ルジャンドル積分を使用して行われます。積分領域は、`control_freqs`に加えて、`sdof`共振周波数の周りで積分の良好な近似を確保するために、`f_n/1.5`および`f_n*1.5`の2つの挿入周波数で分割されます。

関連情報： [`spectral_moments`](@ref)
