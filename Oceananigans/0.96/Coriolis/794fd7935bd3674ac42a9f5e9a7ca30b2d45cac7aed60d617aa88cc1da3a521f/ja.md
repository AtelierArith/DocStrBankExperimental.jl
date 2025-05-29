```
BetaPlane([FT=Float64;] f₀=nothing, β=nothing,
          rotation_rate=Ω_Earth, latitude=nothing, radius=R_Earth)
```

$$
β
$$

-平面コリオリパラメータを返します。$f = f₀ + β y$ で、浮動小数点型 `FT` です。

ユーザーは `f₀` と `β` の両方を指定することができます。または、回転率、半径、中央緯度（$y = 0$ の位置）を指定する3つのパラメータを指定することができ、ここで `β`-平面近似が行われます。

`f₀` と `β` が指定されていない場合、`rotation_rate`、`latitude`、および `radius` から次の関係に従って計算されます：`f₀ = 2 * rotation_rate * sind(latitude)` および `β = 2 * rotation_rate * cosd(latitude) / radius`。

デフォルトでは、`rotation_rate` と惑星の `radius` は地球のものと見なされます。
