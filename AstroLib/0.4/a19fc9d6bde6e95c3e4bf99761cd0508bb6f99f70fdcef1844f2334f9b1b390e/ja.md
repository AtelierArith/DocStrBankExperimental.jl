```
tics(radec_min, radec_max, numx, ticsize[, ra=true]) -> ticsize, incr
```

### 目的

天文学的画像のためのティックマーク間の適切な増分を計算します。

### 説明

表示された画像に赤経または赤緯軸のラベルを付けるために使用します。ティックマーク間の近似距離が入力され、新しい値が計算され、ティックラベル値の単純な増分でティックマーク間の距離が得られます。

### 引数

  * `radec_min` : 最小軸値（度）。
  * `radec_max` : 最大軸値（度）。
  * `numx` : x方向のピクセル数。
  * `ticsize` : ティックマーク間の距離（ピクセル）。
  * `ra`（オプションのブールキーワード）：trueの場合、増分値は時間の分になります。デフォルトはfalseです。

### 出力

2タプル `(ticsize, incr)`：

  * `ticsize` : ティックマーク間の距離（ピクセル）。
  * `incr` : ティックラベルのための増分値。フォーマットはオプションのキーワードに依存します。trueの場合（すなわち赤経の場合）、時間の分で、そうでなければ赤緯の場合は弧度の分になります。

### 例

```jldoctest
julia> using AstroLib

julia> tics(55, 60, 100.0, 1/2)
(0.66, 2.0)

julia> tics(30, 60, 12, 2, true)
(2.75, 30.0)
```

### 注意

この関数のコードはIDL天文学ユーザーライブラリに基づいています。
