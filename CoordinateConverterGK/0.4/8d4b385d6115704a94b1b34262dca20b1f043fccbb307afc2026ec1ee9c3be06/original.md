```
φ , λ = yx2latlon(φ₀, λ₀, N, E)
```

Coordinate transformation between geographic and plane rectangular coordinates on the Gauss-Krüger Projection This function is based on the following documents:         https://www.gsi.go.jp/common/000061216.pdf         https://vldb.gsi.go.jp/sokuchi/surveycalc/surveycalc/algorithm/xy2bl/xy2bl.htm         https://vldb.gsi.go.jp/sokuchi/surveycalc/surveycalc/algorithm/bl2xy/bl2xy.htm

### input arguments

  * φ₀, λ₀ : latitude of origin and central meridian
  * N, E   : plane rectangular coordinates northing and easting

### return values

  * φ , λ  : geographic latitude and longitude

### Examples

```julia-repl
julia> # ANSWER: lat = 36.10404755, lon = 140.08539843

julia> yx2latlon(36.0, 139.83333333, 11573.375, 22694.980)
(36.104047552508895, 140.08539842726532)
```
