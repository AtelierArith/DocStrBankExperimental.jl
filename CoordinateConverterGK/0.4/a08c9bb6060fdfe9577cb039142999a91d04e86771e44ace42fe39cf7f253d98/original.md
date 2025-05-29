```
N, E = latlon2yx(φ₀, λ₀, φ, λ)
```

Coordinate transformation between geographic and plane rectangular coordinates on the Gauss-Krüger Projection This function is based on the following documents:         https://www.gsi.go.jp/common/000061216.pdf         https://vldb.gsi.go.jp/sokuchi/surveycalc/surveycalc/algorithm/xy2bl/xy2bl.htm         https://vldb.gsi.go.jp/sokuchi/surveycalc/surveycalc/algorithm/bl2xy/bl2xy.htm

### input arguments

  * φ₀, λ₀ : latitude of origin and central meridian
  * φ , λ  : geographic latitude and longitude

### return values

  * N, E   : plane rectangular coordinates northing and easting

### Examples

```julia-repl
julia> # ANSWER: y = 11543.6883, x = 22916.2436

julia> latlon2yx(36.0, 139.0+5.0/6.0, 36.103774791666666, 140.08785504166664)
(11543.688321484718, 22916.24355431881)
```
