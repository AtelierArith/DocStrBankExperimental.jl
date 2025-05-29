高域通過画像における位相と振幅をモノジェニックフィルタを用いて計算します。

```
使用法: (phase, orient, E) = highpassmonogenic(img, maxwavelength, n)

引数:           img - 処理する画像。実数またはグレイ要素の2D配列。
           maxwavelength - バターワース高域通過フィルタのカットイン周波数の
                           ピクセル単位の波長。
                       n - バターワースフィルタの次数。この値は
                           整数で1以上である必要があります。値が大きいほど
                           カットオフが鋭くなります。

戻り値:           phase - ローカル位相。値は -pi/2 から pi/2 の間。
                  orient - ローカル方向。値は -pi から pi の間。
                           ローカル位相が +-pi/2 に近い場合、方向は
                           定義が不明確になります。
                       E - 信号のローカルエネルギー、または振幅。
```

`maxwavelength` は配列である場合があり、その場合、出力は `nscales` の長さの出力画像の配列になります。ここで、`nscales = length(maxwavelength)` です。

関連情報: [`bandpassmonogenic`](@ref), [`ppdrc`](@ref), [`monofilt`](@ref)
