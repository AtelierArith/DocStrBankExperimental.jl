```
BetaVector(x::Real,y::Real,z::Real)
```

三次元カルテシアン方向の運動に関連する速度パラメータ（「ベータ」ベクトルと呼ばれる）の空間ベクトルを表します。すなわち、$\vec\beta = (\beta_x, \beta_y, \beta_z)$です。これらの成分は、各$x$、$y$、$z$方向における物体の速度（光速の単位で）に対応します。

ベータベクトル$\vec\beta$の方向に沿ったローレンツブーストは、四元運動量を次のように変換します：

$$
\begin{pmatrix}
p_0\\
p_1\\
p_2\\
p_3
\end{pmatrix} \mapsto
\begin{pmatrix}
    \gamma  (p_0 - \vec\beta \vec p)\\
p_1 + (\frac{\gamma - 1}{\beta^2} \vec\beta\vec p - \gamma  p_0)
 \beta_x\\
p_2 + (\frac{\gamma - 1}{\beta^2} \vec\beta\vec p - \gamma  p_0)
 \beta_y\\
    p_3 + (\frac{\gamma - 1}{\beta^2} \vec\beta\vec p - \gamma  p_0)
 \beta_z\\
\end{pmatrix}
$$

ここで、運動学的因子は$\gamma = 1/\sqrt{1-\beta_x^2}$として与えられます。

## 例

```jldoctest
julia> using QEDcore

julia> beta_vec = BetaVector(0.2,0.3,0.1)
BetaVector{Float64}(0.2, 0.3, 0.1)

julia> boost = Boost(beta_vec)
Boost{BetaVector{Float64}}(BetaVector{Float64}(0.2, 0.3, 0.1))

julia> p = SFourMomentum(4.0,3.0,2.0,1.0)
4-element SFourMomentum with indices SOneTo(4):
 4.0
 3.0
 2.0
 1.0

julia> p_prime = boost(p)
4-element SFourMomentum with indices SOneTo(4):
 2.911484876492837
 2.282803602436349
 0.9242054036545237
 0.6414018012181746

julia> @assert isapprox(p*p,p_prime*p_prime) # 不変質量は保存される
```

## 外部リンク

  * [ローレンツブースト - Wikipedia](https://en.wikipedia.org/wiki/Lorentz_transformation)
  * [PDGレビューにおける運動学](https://pdg.lbl.gov/2024/reviews/rpp2024-rev-kinematics.pdf)
  * [`ROOT::Math:Boost` from ROOT](https://root.cern.ch/doc/master/classROOT_1_1Math_1_1Boost.html)
