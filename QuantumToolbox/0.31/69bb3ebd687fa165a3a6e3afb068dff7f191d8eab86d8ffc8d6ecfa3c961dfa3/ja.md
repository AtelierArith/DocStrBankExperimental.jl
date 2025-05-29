```
DissipativeIsing(Jx::Real, Jy::Real, Jz::Real, hx::Real, hy::Real, hz::Real, γ::Real, latt::Lattice; boundary_condition::Union{Symbol, Val} = Val(:periodic_bc), order::Integer = 1)
```

非弾性イジングモデルのためのJuliaコンストラクタ。関数はハミルトニアンを返します。

$$
\hat{H} = \frac{J_x}{2} \sum_{\langle i, j \rangle} \hat{\sigma}_i^x \hat{\sigma}_j^x + \frac{J_y}{2} \sum_{\langle i, j \rangle} \hat{\sigma}_i^y \hat{\sigma}_j^y + \frac{J_z}{2} \sum_{\langle i, j \rangle} \hat{\sigma}_i^z \hat{\sigma}_j^z + h_x \sum_i \hat{\sigma}_i^x
$$

および崩壊演算子

$$
\hat{c}_i = \sqrt{\gamma} \hat{\sigma}_i^-
$$

# 引数

  * `Jx::Real`: x方向の結合定数。
  * `Jy::Real`: y方向の結合定数。
  * `Jz::Real`: z方向の結合定数。
  * `hx::Real`: x方向の磁場。
  * `hy::Real`: y方向の磁場。
  * `hz::Real`: z方向の磁場。
  * `γ::Real`: 局所的な散逸率。
  * `latt::Lattice`: 格子の幾何学を定義する[`Lattice`](@ref)オブジェクト。
  * `boundary_condition::Union{Symbol, Val}`: 格子の境界条件。可能な入力は、周期的境界条件のための`periodic_bc`と開放境界条件のための`open_bc`です。デフォルト値は`Val(:periodic_bc)`です。
  * `order::Integer`: 最近接サイトの順序。デフォルト値は1です。
