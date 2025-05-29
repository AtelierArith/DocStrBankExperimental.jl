```
spokes_object(imgSize = (256, 256), numSpikes = 21, continuous = true, makeRound = true)
```

2Dまたは3Dのスポークオブジェクトの表現を生成します。

# 引数

  * `imgSize::Tuple{Int, Int}`: 画像のサイズを表す整数のタプル。デフォルトは(256, 256)です。
  * `numSpikes::Int`: スパイクの数を表す整数。デフォルトは21です。
  * `continuous::Bool`: スポークが連続しているかどうかを示すブール値。デフォルトはtrueです。
  * `makeRound::Bool`: オブジェクトが円形であるかどうかを示すブール値。デフォルトはtrueです。

# 戻り値

  * `obj2::Array{Float64}`: スポークオブジェクトを表す2Dまたは3D配列。

# 例

```jldoctest
spokes_object((512, 512), 30, false, false)
```
