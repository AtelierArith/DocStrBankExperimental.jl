```
gridfunction(ID::Int, n::Int, T::Type; h=1, p=5, polynom=[0,1], deriv=0)
```

`CamiDiff` offers three internal grid functions:

  * `ID = 1`: exponential grid function,

$$
    g(t) = \rm{exp}(t) - 1
$$

  * `ID = 2`: truncated-exponential grid function of degree `p` (linear grid for `p = 1`),

$$
    g(t) = t + \frac{1}{2}t^2 + ⋯ + \frac{1}{p!}t^p
$$

  * `ID = 3`: linear grid function,

$$
    g(t) = t
$$

  * `ID = 4`: polynomial grid function of degree `p = length(c)-1` defined by its [`CamiMath.polynom`](@extref) vector $c = [c_0, c_1,c_2,⋯\ c_p]$,

$$
    g(t) = c_0 + c_1 t + c_2 t^2 + ⋯ + c_p t^p,
$$

with $c_0 ≡ 0$ because, *by definition*, all [`gridfunction`](@ref)`s` run through the origin, $g(0) = 0$. 

The actual [`Grid`](@ref) is given by 

$$
    r[n] = r_0 * g(t[n]),
$$

where $t[n] = (n-1) * h$ is the *ticks function* for the unit-based indexing of [Julia](http://julialang.org).

NB. All [`gridfunction`](@ref)`s` satisfy the properties $t[1] = 0$ and $r[1] = 0$.

#### Examples:

```
julia> h = 0.1; r0=1.0; N=4; T=Float64;

julia> r = [r0*gridfunction(1, n, T; h) for n=1:N]; println("r = ", r)
r = [0.0, 0.10517091807564771, 0.22140275816016985, 0.3498588075760032]

julia> r′= r0 .* [r0*gridfunction(1, n, T; h, deriv=1) for n=1:N]; println("r′= ", r′)
r′ = [0.1, 0.11051709180756478, 0.122140275816017, 0.13498588075760032]

julia> r′′= [r0*gridfunction(1, n, T; h, deriv=2) for n=1:N]; println("r′′= ", r′′)
r′′ = [0.010000000000000002, 0.011051709180756479, 0.012214027581601701, 0.013498588075760034]

julia> r = [r0*gridfunction(4, n, T; h, polynom=[0,0,1]) for n=1:N]; println("r = ", r)
r = [0.0, 0.010000000000000002, 0.04000000000000001, 0.09000000000000002]

julia> r′= [r0*gridfunction(4, n, T; h, polynom=[0,0,1], deriv=1) for n=1:N]; println("r′= ", r′)
r′= [0.0, 0.020000000000000004, 0.04000000000000001, 0.06000000000000001]

julia> r′′= [r0*gridfunction(4, n, T; h, polynom=[0,0,1], deriv=2) for n=1:N]; println("r′′= ", r′′)
r′′= [0.020000000000000004, 0.020000000000000004, 0.020000000000000004, 0.020000000000000004]
```
