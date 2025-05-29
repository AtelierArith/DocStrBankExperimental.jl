```julia
GetConductivity!(Cond::Conductivity, as::Vector{Int64}  ; get_velocity::Bool = false, get_spectral::Bool = false)
```

フルDC導電率を計算します。ハミルトニアンの速度行列を計算するオプションのブール値、スペクトル関数も計算するオプションのブール値があります。
