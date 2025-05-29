```
gridfunction(ID::Int, n::Int, T::Type; h=1, p=5, polynom=[0,1], deriv=0)
```

`CamiDiff` は三つの内部グリッド関数を提供します：

  * `ID = 1`: 指数グリッド関数、

$$
    g(t) = \rm{exp}(t) - 1
$$

  * `ID = 2`: 次数 `p` の切断指数グリッド関数（`p = 1` の場合は線形グリッド）、

$$
    g(t) = t + \frac{1}{2}t^2 + ⋯ + \frac{1}{p!}t^p
$$

  * `ID = 3`: 線形グリッド関数、

$$
    g(t) = t
$$

  * `ID = 4`: ベクトル [$c = [c_0, c_1,c_2,⋯\ c_p]$](@extref) によって定義された次数 `p = length(c)-1` の多項式グリッド関数、

$$
    g(t) = c_0 + c_1 t + c_2 t^2 + ⋯ + c_p t^p,
$$

ここで $c_0 ≡ 0$ であるのは、*定義により*、すべての [`gridfunction`](@ref)`s` が原点を通るため、$g(0) = 0$ です。

実際の [`Grid`](@ref) は次のように与えられます。

$$
    r[n] = r_0 * g(t[n]),
$$

ここで $t[n] = (n-1) * h$ は [Julia](http://julialang.org) の単位ベースのインデックス付けのための *ticks function* です。

注意：すべての [`gridfunction`](@ref)`s` は $t[1] = 0$ および $r[1] = 0$ の特性を満たします。

#### 例：

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
