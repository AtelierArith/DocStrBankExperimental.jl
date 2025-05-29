```
φ , λ = yx2latlon(φ₀, λ₀, N, E)
```

ガウス・クリューガー投影における地理座標と平面直交座標間の座標変換。この関数は以下の文書に基づいています:         https://www.gsi.go.jp/common/000061216.pdf         https://vldb.gsi.go.jp/sokuchi/surveycalc/surveycalc/algorithm/xy2bl/xy2bl.htm         https://vldb.gsi.go.jp/sokuchi/surveycalc/surveycalc/algorithm/bl2xy/bl2xy.htm

### 入力引数

  * φ₀, λ₀ : 原点の緯度と中央子午線
  * N, E   : 平面直交座標の北方向および東方向の座標

### 戻り値

  * φ , λ  : 地理的緯度と経度

### 例

```julia-repl
julia> # ANSWER: lat = 36.10404755, lon = 140.08539843

julia> yx2latlon(36.0, 139.83333333, 11573.375, 22694.980)
(36.104047552508895, 140.08539842726532)
```
