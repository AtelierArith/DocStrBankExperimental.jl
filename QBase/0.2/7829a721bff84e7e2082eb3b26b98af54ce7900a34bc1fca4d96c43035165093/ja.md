```
qubit_rotation( θ :: Real; axis="x" :: String ) :: Unitary{Complex{Float64}}
```

ブロッホ球に沿ったキュービット回転を行うユニタリを返します。`θ`は回転の角度を指定し、`axis`（`"x"`、`"y"`、`"z"`）はキュービットが回転する直交軸を指定します。
