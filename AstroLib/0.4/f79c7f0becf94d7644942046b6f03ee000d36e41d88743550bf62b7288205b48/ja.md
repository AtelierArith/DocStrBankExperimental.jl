```
polrec(radius, angle[, degrees=true]) -> x, y
```

### 目的

2D極座標を直交座標に変換します。

### 説明

これは`recpol`の部分的逆関数です。

### 引数

  * `radius`: 点の放射座標。スカラーまたは配列である可能性があります。
  * `angle`: 点の角度座標。`radius`と同じ長さのスカラーまたは配列である可能性があります。
  * `degrees`（オプションのブールキーワード）：`true`の場合、`angle`は度数法であると仮定され、それ以外の場合はラジアンです。デフォルトは`false`です。

必須引数は2タプル`(radius, angle)`としても渡すことができるため、`recpol(polrec(radius, angle))`を実行することが可能です。

### 出力

入力の直交座標を持つ2タプル`(x, y)`。`radius`と`angle`が配列の場合、`x`と`y`は`radius`と`angle`と同じ長さの配列になります。

### 例

極座標$(r, φ) = (1.7, 227)$を持つ点の直交座標$(x, y)$を取得します。角度$φ$は度数法で表現されます。

```jldoctest
julia> using AstroLib

julia> x, y = polrec(1.7, 227, degrees=true)
(-1.1593972121062475, -1.2433012927525897)
```
