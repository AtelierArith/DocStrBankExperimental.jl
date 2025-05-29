```
radec(ra::Real, dec::Real[, hours=false]) -> ra_hours, ra_minutes, ra_seconds, dec_degrees, dec_minutes, dec_seconds
```

### 目的

右昇と赤緯を十進法から性分法単位に変換します。

### 説明

変換は、右昇に対して性分法の時間、赤緯に対して性分法の度数に行われます。

### 引数

  * `ra`: 十進法の右昇、スカラーまたは配列。オプションのキーワード `hours` が `true` に設定されていない限り、度数で表現されます。
  * `dec`: 十進法の度数で表現された赤緯、スカラーまたは配列、`ra` と同じ数の要素を持ちます。
  * `hours` (オプションのブールキーワード): `false`（デフォルト）の場合、`ra` は度数で与えられていると仮定されます。それ以外の場合、`ra` は時間で表現されていると仮定されます。

### 出力

`AbstractFloat` の6タプル:

```
(ra_hours, ra_minutes, ra_seconds, dec_degrees, dec_minutes, dec_seconds)
```

`ra` と `dec` が配列の場合、出力の6タプルの各要素も同じ次元の配列になります。

### 例

シリウスの空における位置は (ra, dec) = (6.7525, -16.7161) で、右昇は時間で表現されています。その性分法表現は次のようになります。

```jldoctest
julia> using AstroLib

julia> radec(6.7525, -16.7161, hours=true)
(6.0, 45.0, 9.0, -16.0, 42.0, 57.9600000000064)
```
