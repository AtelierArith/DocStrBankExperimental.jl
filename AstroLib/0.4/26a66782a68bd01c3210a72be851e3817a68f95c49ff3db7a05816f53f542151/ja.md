```
recpol(x, y[, degrees=false]) -> radius, angle
```

### 目的

2D直交座標を極座標に変換します。

### 説明

これは`polrec`の部分的な逆関数です。

### 引数

  * `x`: 点の横座標。スカラーまたは配列である可能性があります。
  * `y`: 点の縦座標。スカラーまたは`x`と同じ長さの配列である可能性があります。
  * `degrees`（オプションのブールキーワード）：`true`の場合、出力される`angle`は度で与えられ、それ以外の場合はラジアンで与えられます。デフォルトは`false`です。

必須の引数は2タプル`(x, y)`としても渡すことができるため、`polrec(recpol(x, y))`を実行することが可能です。

### 出力

入力の極座標を持つ2タプル`(radius, angle)`。座標`angle`は、`degrees=false`の場合は範囲$[-π, π]$に、`degrees=true`の場合は範囲$[-180, 180]$にあります。

`x`と`y`が配列の場合、`radius`と`angle`は`radius`と`angle`と同じ長さの配列になります。

### 例

直交座標$(x, y) = (2.24, -1.87)$の点の極座標$(r, φ)$を計算します。

```jldoctest
julia> using AstroLib

julia> r, phi = recpol(2.24, -1.87)
(2.9179616172938263, -0.6956158538564537)
```

角度$φ$はラジアンで与えられます。
