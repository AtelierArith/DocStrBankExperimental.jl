バンドパス画像における位相と振幅をモノジェニックフィルタを用いて計算します。

```
Usage: (phase, orient, E) = bandpassmonogenic(img, minwavelength, maxwavelength, n)

Arguments:           img - 処理する画像。実数またはグレイ要素の2D配列。
           minwavelength - } カットインおよびカットアウト周波数のピクセル単位の波長
           maxwavelength - } バターワースバンドパスフィルタの。
                       n - バターワースフィルタの次数。この値は
                           整数で1以上です。値が大きいほどカットオフが鋭くなります。

Returns:           phase - ローカル位相。値は -pi/2 から pi/2 の間。
                  orient - ローカル方向。値は -pi から pi の間。
                           ローカル位相が +-pi/2 に近い場合、方向は定義が不明確になります。
                       E - 信号のローカルエネルギー、または振幅。
```

`minwavelength` と `maxwavelength` は（同じ長さの）配列であることができ、その場合、出力は `nscales` の長さの出力画像の配列になります。ここで、`nscales = length(maxwavelength)` です。

参照: [`highpassmonogenic`](@ref), [`ppdrc`](@ref), [`monofilt`](@ref)
