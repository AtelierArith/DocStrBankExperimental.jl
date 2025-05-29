```
function IncompressibleNavierStokesProblem(
    dimension::Int = 2;
    viscosity = 1.0,
    nonlinear::Bool = false,
    newton::Bool = false,
    nopressureconstraint::Bool = false,
    pmean = 0)
```

指定された次元とグローバルに一定の粘度パラメータのための非圧縮性（ナビエ-ストークス）方程式のPDEDescriptionを作成します。nonlinear = trueの場合、非線形対流項がPDEDescriptionに追加されます。また、newton = trueの場合、対流項のためのニュートン反復が考案されます。
