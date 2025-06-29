```
FIRWindow(window; scale=true)
```

ウィンドウ `window` を使用したFIRフィルタ設計で、ベクトルの長さは結果のフィルタのタップ数と一致します。

`scale` が `true`（デフォルト）の場合、設計されたFIRフィルタは以下の条件を満たすようにスケーリングされます：

  * [`Lowpass`](@ref) および [`Bandstop`](@ref) フィルタの場合、周波数応答は0（DC）で1になります。
  * [`Highpass`](@ref) フィルタの場合、周波数応答はナイキスト周波数で1になります。
  * [`Bandpass`](@ref) フィルタの場合、周波数応答は通過帯域の中心で1になります。
