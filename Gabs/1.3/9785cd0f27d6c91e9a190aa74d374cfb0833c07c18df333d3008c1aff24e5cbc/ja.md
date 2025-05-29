```
logarithmic_negativity(state::GaussianState, indices::Union{Integer, AbstractVector{<:Integer}}; tola::Real = 0, tolb::Real = 128 * eps(1))
```

ガウス状態の部分の対数的負性を計算します。これは次のように定義されます。

$$
N(\rho) = \log\|\rho^{T_B}\|_1 = - \sum_i \log(2 \tilde{v}_i^<)
$$

ここで、$\log$は自然対数を示し、$\tilde{v}_i^<$は$\mathbf{\tilde{V}}/\hbar$のシンプレクティックスペクトルであり、$< 1/2$です。

ここで、$\mathbf{\tilde{V}} = \mathbf{T} \mathbf{V} \mathbf{T}$であり、

$$
\forall k : \mathbf{T} q_k = q_k
\forall k \in \mathrm{B} : \mathbf{T} p_k = -p_k
\forall k \notin \mathrm{B} : \mathbf{T} p_k = p_k
$$

# 引数

  * `state`: 対数的負性を計算するガウス状態。
  * `indices`: 整数またはそのコレクションで、バイナリパーティションを指定します。
  * `tola`: $\log(x)$を計算する際のカットオフ$0$以上の許容誤差（含む）。
  * `tolb`: $\log(x)$を計算する際のカットオフ$1$以下の許容誤差（含む）。

```
