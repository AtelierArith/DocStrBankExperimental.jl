調和（正弦）照明パターンの形

$$
    I(\vec{r})=1+{\frac{m}{2}}\cos\left(2π⋅ (kₓ⋅(\vec{r})ₓ + k_y ⋅ (\vec{r})_y) + \phi\right)
$$

```
Harmonic(m::Real, θ::Real, ν::Frequency, ϕ::Real)
Harmonic(m::Real, (ν_x, ν_y)::Tuple{Frequency,Frequency}, ϕ::Real)
Harmonic(m::Real, (ν_x, ν_y)::Tuple{Real,Real}, ϕ::Real, Δxy::Length)
Harmonic(m::Real, (ν_x, ν_y)::Tuple{Real,Real}, ϕ::Real, (Δx, Δy)::Tuple{Length,Length})

Harmonic(m::Real, θ::Real, λ::Length, ϕ::Real)
Harmonic(m::Real, (λ_x, λ_y)::Tuple{Length,Length}, ϕ::Real)
Harmonic(m::Real, θ::Real, λ::Real, ϕ::Real, Δxy::Length)
Harmonic(m::Real, θ::Real, λ::Real, ϕ::Real, (Δx, Δy)::Tuple{Length,Length})

Harmonic(m::Real, (δ_x, δ_y)::Tuple{Real, Real}, size::Union{Tuple{Real, Real}, Real}, ϕ::Real, Δxy::Length)
Harmonic(m::Real, (δ_x, δ_y)::Tuple{Real, Real}, size::Union{Tuple{Real, Real}, Real}, ϕ::Real, (Δx, Δy)::Tuple{Length,Length})
```

パラメータの型は `Real`、[`Frequency`](@ref) または [`Unitful.Length`](@extref Unitful Length) であり、次のことを示します：

  * `m`: 変調係数
  * `θ`: 方向角（$x$-軸から）(`\theta`)
  * `ν`: 周波数 (`\nu`)
  * `(ν_x, ν_y)`: 波ベクトル（物理単位での「シフト」） ($(ν_x, ν_y) = (\sin(θ) ⋅ ν , \, \cos(θ) ⋅ ν)$)
  * `(δ_x, δ_y)`: ピクセルでのシフト
  * `size`: シフト `(δ_x, δ_y)` が決定される取得画像のサイズ
  * `λ`: 波長 (`\lambda`)
  * `(λ_x, λ_y)`: 波峰ベクトル ($(λ_x, λ_y) = (\sin(θ) ⋅ λ , \, \cos(θ) ⋅ λ)$)
  * `ϕ`: 位相オフセット (`\phi`)
  * `Δxy` または `(Δx, Δy)`: $x$-軸および $y$-軸のピクセルサイズ

# 例

```jldoctest
julia> h1 = Harmonic(1, π/2, 1/(2*61u"nm"), π/4)
Harmonic2D(m=1.0, θ=1.57, ν=0.0082 nm^-1, ϕ=0.785)

julia> h2 = Harmonic(1, (0u"nm^-1", 1/(2*61u"nm")), π/4);

julia> h3 = Harmonic(1, (0, 1/2), π/4, 61u"nm");

julia> h4 = Harmonic(1, (0, 1/4), π/4, (61u"nm", 30.5u"nm"));

julia> h5 = Harmonic(1, π/2, 2*61u"nm", π/4);

julia> h6 = Harmonic(1, (0u"nm", 2*61u"nm"), π/4);

julia> # h7 = Harmonic(1, π/2, 2, π/4, 61u"nm") # FIX

julia> # h8 = Harmonic(1, π/2, 2, π/4, (61u"nm", 61u"nm")) # FIX

julia> h9 = Harmonic(1, (0, 256), (512, 512), π/4, 61u"nm");

julia> h10 = Harmonic(1, (0, 128), (512, 512), π/4, (61u"nm", 30.5u"nm"));

julia> h1 == h2 == h3 == h4 == h5 == h6 == h9 == h10
true
```
