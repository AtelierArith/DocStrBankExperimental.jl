```
KarmanTrefftzMap(ν,ϵ,δ,C[;N = 200]) <: ConformalMap
```

Create a map from the exterior of the unit circle to the exterior of a Karman-Trefftz airfoil.

The form of the mapping is

$$
\frac{z-\nu C}{z+\nu C}  =
\left(\frac{\tilde{\zeta}-C}{\tilde{\zeta}+C}\right)^\nu
$$

where $\tilde{\zeta}$ are the coordinates in an intermediate plane, in which the circle is of radius $a$ and centered at $\epsilon C e^{i\delta}$:

$$
\tilde{\zeta} = \epsilon C e^{i\delta} + a \zeta
$$

Note that $a/C \geq 1$ and is determined by the choices for $\epsilon$ and $\delta$.

The trailing edge angle, $(2-\nu)\pi$ is specified by $\nu$. The thickness is controlled by $\epsilon C \cos\delta$ and the camber by $\epsilon C \sin\delta$. The airfoil chord length is approximately $4C$. Generally, $\epsilon$ should be much smaller than 1 and $\delta$ between $\pi/2$ and $\pi$.

The resulting map `m` can be evaluated at a single or a vector of points `ζ` with `m(ζ)`.

# Example

```jldoctest
julia> ν = 1.9; ϵ = 0.1; δ = π; C = 0.25;

julia> m = KarmanTrefftzMap(ν,ϵ,δ,C)
Karman-Trefftz map

julia> ζ = [1.0+3.0im,-2.0-2.0im,0.0+1.1im];

julia> m(ζ)
3-element Array{Complex{Float64},1}:
   0.268188+0.764722im
  -0.624265-0.502634im
 -0.0390996+0.126737im
```
