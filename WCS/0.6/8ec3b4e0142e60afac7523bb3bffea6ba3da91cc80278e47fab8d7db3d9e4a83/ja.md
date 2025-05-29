```
WCSTransform(naxis; kwds...)
```

与えられた軸の数 `naxis` で WCS 変換を構築します。キーワード引数を渡すことで、変換のさまざまな属性を設定できます。キーワード引数を指定することは、構築後にそれらを設定することと同等です：

```
julia> wcs = WCSTransform(2; crpix=[1000., 1000.])
```

は次のように等価です：

```
julia> wcs = WCSTransform(2)

julia> wcs.crpix = [1000., 1000.]
```

# プロパティ

以下は `WCSTransform` の公開プロパティの全リストです。

|   キーワード | 型                                         | 説明                           |
| -------:|:----------------------------------------- |:---------------------------- |
|   naxis | `Int`                                     | 次元の数                         |
|   crval | `Vector{Float}[naxis]`                    | 基準点での座標値                     |
|   crpix | `Vector{Float}[naxis]`                    | ピクセル単位での基準点の配列位置             |
|   cdelt | `Vector{Float}[naxis]`                    | 基準点での座標の増分                   |
|   crder | `Vector{Float}[naxis]`                    | 座標のランダム誤差                    |
|   csyer | `Vector{Float}[naxis]`                    | 座標の系統的誤差                     |
|   ctype | `Vector{String}[naxis]`                   | 軸のタイプ（8文字）                   |
|   crota | `Vector{Float}[naxis]`                    | 指定された座標タイプからの回転              |
|   cunit | `Vector{String}[naxis]`                   | 軸の単位                         |
|   cunit | `Vector{String}[naxis]`                   | 軸の名前                         |
|      pc | `Matrix{Float}[naxis, naxis]`             | 線形変換行列                       |
|      cd | `Matrix{Float}[naxis, naxis]`             | 線形変換行列（スケール付き）               |
| equinox | `Float`                                   | 動的赤道または黄道座標系に関連する春分点         |
| latpole | `Float`                                   | 天体の極の固有緯度                    |
| lonpole | `Float`                                   | 天体の極の固有経度                    |
|  mjdavg | `Float`                                   | `DATE-AVG` に対応する修正ユリウス日      |
|  mjdobs | `Float`                                   | `DATE-OBS` に対応する修正ユリウス日      |
| restfrq | `Float`                                   | 静止周波数（Hz）                    |
| restwav | `Float`                                   | 静止波長（m）                      |
| velangl | `Float`                                   | 速度角                          |
| velosys | `Float`                                   | 相対半径速度                       |
| zsource | `Float`                                   | ソースの赤方偏移                     |
|  colnum | `Int`                                     | この WCS に関連する FITS バイナリテーブルの列 |
| dateavg | `String`                                  | 観測日の代表的な中間点                  |
| dateobs | `String`                                  | 観測日の開始                       |
| radesys | `String`                                  | 赤道または黄道座標系のタイプ               |
| specsys | `String`                                  | スペクトル基準フレーム（静止の基準）           |
| ssysobs | `String`                                  | スペクトル基準フレーム                  |
| ssyssrc | `String`                                  | 赤方偏移のためのスペクトル基準フレーム          |
| wcsname | `String`                                  | この座標表現の名前                    |
|  obsgeo | `Vector{Float}[3]` または `Vector{Float}[6]` | 標準的な地球参照フレームにおける観測者の位置       |
|     alt | `String`                                  | 代替座標記述のための文字コード              |
