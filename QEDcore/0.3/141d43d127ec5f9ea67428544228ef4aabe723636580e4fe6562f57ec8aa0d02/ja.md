```
BetaX(beta::T) where {T<:Real}
```

これは、通常$\beta_x$と表記されるx軸に沿ったローレンツブーストに関連するベータパラメータを表します。

x軸に沿ったブーストの変換は次のようになります：

$$
\begin{pmatrix}
p_0\\
p_1\\
p_2\\
p_3
\end{pmatrix} \mapsto
\begin{pmatrix}
\gamma (p_0 - \beta_x p_1)\\
\gamma (p_1 - \beta_x p_0)\\
p_2\\
p_3
\end{pmatrix}
$$

ここで、運動学的因子は$\gamma = 1/\sqrt{1-\beta_x^2}$で与えられます。

## 例

```jldoctest
julia> using QEDcore

julia> beta_x = BetaX(0.5)
BetaX{Float64}(0.5)

julia> boost = Boost(beta_x)
Boost{BetaX{Float64}}(BetaX{Float64}(0.5))

julia> p = SFourMomentum(4,3,2,1)
4-element SFourMomentum with indices SOneTo(4):
 4.0
 3.0
 2.0
 1.0

julia> p_prime = boost(p)
4-element SFourMomentum with indices SOneTo(4):
 2.886751345948129
 1.1547005383792517
 2.0
 1.0

julia> @assert isapprox(p*p,p_prime*p_prime) # 不変質量は保存される
```

## 外部リンク

  * [ローレンツブースト - Wikipedia](https://en.wikipedia.org/wiki/Lorentz_transformation)
  * [PDGレビューの運動学](https://pdg.lbl.gov/2024/reviews/rpp2024-rev-kinematics.pdf)
