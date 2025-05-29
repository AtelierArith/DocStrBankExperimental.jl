```
BetaZ(beta::T) where {T<:Real}
```

z軸に沿ったローレンツブーストに関連するベータパラメータを表し、一般に$\beta_z$として示されます。

z軸に沿ったブーストの変換は次のようになります：

$$
\begin{pmatrix}
p_0\\
p_1\\
p_2\\
p_3
\end{pmatrix} \mapsto
\begin{pmatrix}
\gamma (p_0 - \beta_z p_3)\\
p_1\\
p_2\\
\gamma (p_3 - \beta_z p_0)\\
\end{pmatrix}
$$

ここで、運動学的因子は$\gamma = 1/\sqrt{1-\beta_z^2}$として与えられます。

## 例

```jldoctest
julia> using QEDcore

julia> using Random

julia> RNG = MersenneTwister(1234)
MersenneTwister(1234)

julia> beta_z = BetaZ(0.5)
BetaZ{Float64}(0.5)

julia> boost = Boost(beta_z)
Boost{BetaZ{Float64}}(BetaZ{Float64}(0.5))

julia> p = SFourMomentum(4,3,2,1)
4-element SFourMomentum with indices SOneTo(4):
 4.0
 3.0
 2.0
 1.0

julia> p_prime = boost(p)
4-element SFourMomentum with indices SOneTo(4):
  4.041451884327381
  3.0
  2.0
 -1.1547005383792517

julia> @assert isapprox(p*p,p_prime*p_prime) # 不変質量は保存されます

```

## 外部リンク

  * [ローレンツブースト - Wikipedia](https://en.wikipedia.org/wiki/Lorentz_transformation)
  * [PDGレビューにおける運動学](https://pdg.lbl.gov/2024/reviews/rpp2024-rev-kinematics.pdf)
