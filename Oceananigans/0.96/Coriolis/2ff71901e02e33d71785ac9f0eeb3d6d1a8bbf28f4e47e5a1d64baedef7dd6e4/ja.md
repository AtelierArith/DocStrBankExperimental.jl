```
NonTraditionalBetaPlane(FT=Float64;
                        fz=nothing, fy=nothing, β=nothing, γ=nothing,
                        rotation_rate=Ω_Earth, latitude=nothing, radius=R_Earth)
```

ユーザーは直接 `fz`、`fy`、`β`、`γ`、および `radius` を指定するか、惑星の回転率と半径、非伝統的な `β`-平面近似が行われる中央緯度（$y = 0$ の場所）を指定するための3つのパラメータ `rotation_rate`、`latitude`（度単位）、および `radius` を指定できます。

`fz`、`fy`、`β`、および `γ` が指定されていない場合、それらは `rotation_rate`、`latitude`、および `radius` に基づいて次の関係式に従って計算されます：`fz = 2 * rotation_rate * sind(latitude)`、`fy = 2 * rotation_rate * cosd(latitude)`、`β = 2 * rotation_rate * cosd(latitude) / radius`、および `γ = - 4 * rotation_rate * sind(latitude) / radius`。

デフォルトでは、`rotation_rate` と惑星の `radius` は地球のものと仮定されます。
