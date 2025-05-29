```
absolutemagnitude(sol::NEOSolution{T, T}, params::NEOParameters{T}) where {T <: Real}
```

軌道 `sol` の絶対等級とその標準誤差を返します。この関数は小惑星のための線形 H および G モデルを使用します。

!!! reference
    See https://minorplanetcenter.net/iau/ECS/MPCArchive/1985/MPC_19851227.pdf.

