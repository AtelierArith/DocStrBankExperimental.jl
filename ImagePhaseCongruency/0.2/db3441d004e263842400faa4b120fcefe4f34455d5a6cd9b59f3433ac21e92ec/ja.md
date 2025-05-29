位相が一致する円形正弦波グレーティングを生成します。

特徴検出器の応答の等方性をテストするのに便利です。

```
Usage:    img = circsine(sze; wavelength = 40, nscales = 50, ampexponent = -1,
                          offset = 0, p = 2, trim = false)

Arguments:
   sze::Integer  - 生成される正方形画像のサイズ。デフォルトは512。

Keyword arguments:
 wavelength::Real - 正弦波の波長（ピクセル単位）。デフォルトは40。
 nscales::Integer - 信号を構成するために使用されるフーリエ成分の数。
                    単純な正弦波を希望する場合は通常1、位相が一致する
                    波形を構築したい場合は50を超えます。デフォルトは50。
ampexponent::Real - 周波数に対する振幅の減衰指数。
                    -1の値は、振幅が周波数に反比例することを生成します
                    （オフセットが0の場合、ステップ特徴が生成されます）
                    -2の値とπ/2のオフセットは三角波形を生成します。デフォルトは-1;
     offset::Real - 特徴が生成される位相一致の角度。
                    これは特徴のタイプを制御します。
                    ステップ状の特徴には0、線/三角形状の特徴にはπ/2。
                    デフォルトは0。nscales = 1の場合は、中心での連続性を得るために
                    π/2を使用します。
      p::Integer  - 中心からの半径を計算するために使用するノルムを指定する
                    オプションのパラメータ。デフォルトは2で、円形パターンを生成します。
                    大きな値は正方形のパターンを生成します。
      trim::Bool  - 角から切り取られた円形パターンを希望するかどうかを示す
                    オプションのブールフラグ。デフォルトはfalse。
Returns:
   img::Array{Float64,2} - テスト画像。

Examples:
> circsine(nscales = 1) - 単純な円形正弦波パターン
> circsine(nscales = 50, ampexponent = -1, offset =  0)     - 正方形波形
> circsine(nscales = 50, ampexponent = -2, offset = pi/2)   - 三角波形
> circsine(nscales = 50, ampexponent = -1.5, offset = pi/4) - 正方形と三角形の間の何か
> circsine(nscales = 50, ampexponent = -1.5, offset = 0)    - 正方形のように見えるがそうではない。
```

参照: [`starsine`](@ref), [`step2line`](@ref)
