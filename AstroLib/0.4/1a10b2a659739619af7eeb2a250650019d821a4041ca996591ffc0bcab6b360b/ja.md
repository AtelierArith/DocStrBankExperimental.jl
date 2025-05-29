```
sphdist(long1, lat1, long2, lat2[, degrees=true]) -> angular_distance
```

### 目的

球面上の点間の角距離。

### 引数

  * `long1`: 点1の経度
  * `lat1`: 点1の緯度
  * `long2`: 点2の経度
  * `lat2`: 点2の緯度
  * `degrees` (オプションのブールキーワード): `true` の場合、出力距離を含むすべての角度は度数法であると仮定され、それ以外の場合はすべてラジアンであると仮定されます。デフォルトは `false` です。

### 出力

点1と点2の間の球面上の角距離を `AbstractFloat` として返します。`degrees` キーワードが `true` に設定されていない限り、ラジアンで表現されます。

### 例

```jldoctest
julia> using AstroLib

julia> sphdist(120, -43, 175, +22)
1.5904422616007134
```

### 注意事項

  * `gcirc` 関数は `sphdist` に似ていますが、天文学的なアプリケーションにはより適しているかもしれません。

この関数のコードは IDL Astronomy User's Library に基づいています。
