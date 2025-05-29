```julia
struct Covariance
```

共分散の上三角要素。有限回転の場合はラジアン²、オイラーベクトルの場合はラジアン²/Myr²で表現されます。

# 例:

```julia-repl
julia> PlateKinematics.Covariance()
PlateKinematics.Covariance(0, 0, 0, 0, 0, 0)

julia> PlateKinematics.Covariance(1, 2, 3, 4, 5, 6)
PlateKinematics.Covariance(1, 2, 3, 4, 5, 6)

julia> array = [1, 2, 3, 4, 5, 6];
julia> PlateKinematics.Covariance(array)
PlateKinematics.Covariance(1, 2, 3, 4, 5, 6)
```
