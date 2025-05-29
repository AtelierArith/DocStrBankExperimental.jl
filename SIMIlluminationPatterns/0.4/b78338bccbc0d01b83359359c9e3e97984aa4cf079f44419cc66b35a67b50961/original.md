Harmonic (sinusoidal) illumination pattern in the form

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

Parameters have types `Real`, [`Frequency`](@ref) or [`Unitful.Length`](@extref Unitful Length) and denote:

  * `m`: modulation factor
  * `θ`: orientation angle (from the $x$-axis) (`\theta`)
  * `ν`: frequency (`\nu`)
  * `(ν_x, ν_y)`: wave vector ('shift' in physical units) ($(ν_x, ν_y) = (\sin(θ) ⋅ ν , \, \cos(θ) ⋅ ν)$)
  * `(δ_x, δ_y)`: shift in pixels
  * `size`: size of acquisition image, from which the shift `(δ_x, δ_y)` is determined
  * `λ`: wavelength (`\lambda`)
  * `(λ_x, λ_y)`: wavepeak vector ($(λ_x, λ_y) = (\sin(θ) ⋅ λ , \, \cos(θ) ⋅ λ)$)
  * `ϕ`: phase offset (`\phi`)
  * `Δxy` or `(Δx, Δy)`: $x$-axis and $y$-axis pixel sizes

# Examples

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
