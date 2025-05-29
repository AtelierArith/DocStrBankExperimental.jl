位相が一致した星型正弦波グレーティングを生成します。

特徴検出器の線の接合部での動作をテストするのに便利です。

```
Usage:    img = starsine(sze; ncycles=10, nscales=50, ampexponent=-1, offset=0)

Argument:
     sze::Integer - 生成される正方形画像のサイズ。デフォルトは512。

Keyword arguments:
    ncycles::Real - 中心点周辺の正弦波サイクルの数。
                    通常は整数ですが、任意の値を使用できます。
 nscales::Integer - 信号を構成するために使用されるフーリエ成分の数。
                    単純な正弦波を望む場合は通常1、位相が一致した
                    波形を構築したい場合は50以上です。デフォルトは50。
ampexponent::Real - 周波数に対する振幅の減衰指数。
                    -1の値は振幅が周波数に反比例することを生成します（これにより、オフセットが0の場合はステップ特徴が生成されます）
                    -2の値とオフセットがpi/2の場合は三角波形になります。
     offset::Real - 星パターンの特徴が生成される位相の角度。
                    これは特徴のタイプを制御します。
                    ステップ状の特徴には0、線/三角形状の特徴にはpi/2を使用します。
Returns:
   img::Array{Float64,2} - テスト画像。

Examples:
> starsine(nscales = 1) - 中心から放射状に広がる単純な正弦波パターン。
                          それを少し回転させたい場合は'offset'を使用します。
> starsine(nscales = 50, ampexponent = -1, offset =  0)     - 正方形波形
> starsine(nscales = 50, ampexponent = -2, offset = pi/2)   - 三角波形
> starsine(nscales = 50, ampexponent = -1.5, offset = pi/4) - 正方形と三角形の間の何か
> starsine(nscales = 50, ampexponent = -1.5, offset = 0)    - 正方形のように見えますが、そうではありません。
```

参照: [`circsine`](@ref), [`step2line`](@ref)
