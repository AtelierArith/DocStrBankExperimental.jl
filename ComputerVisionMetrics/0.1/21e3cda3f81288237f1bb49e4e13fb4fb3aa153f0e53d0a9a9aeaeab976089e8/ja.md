## `hausdorff_metric`

```julia
hausdorff_metric(
    prediction::AbstractArray, ground_truth::AbstractArray;
    per::Union{Nothing, Real}=nothing, directed::Bool=false
)
```

2つのマスク、`prediction`と`ground_truth`の間のハウスドルフ距離を計算します。

この関数は、提供される引数に応じて複数のメソッドを持っています：

1. `per`なし：標準のハウスドルフ距離を計算します。
2. `per`あり：指定されたパーセンタイルでのハウスドルフ距離を計算します。

#### 引数

  * `prediction`: 予測マスク、`::Bool`または`::Int`の2Dまたは3D配列。
  * `ground_truth`: グラウンドトゥルースマスク、`::Bool`または`::Int`の2Dまたは3D配列。
  * `per`: ハウスドルフ距離のパーセンタイル（オプション）。
  * `directed`: `true`の場合、片側のハウスドルフを計算します。デフォルトは`false`です。

#### 戻り値

  * ハウスドルフ距離または指定されたパーセンタイルでのハウスドルフ距離。
