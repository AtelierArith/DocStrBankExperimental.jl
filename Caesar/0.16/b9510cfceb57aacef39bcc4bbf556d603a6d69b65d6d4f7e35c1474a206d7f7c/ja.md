```julia
struct ScanMatcherPose2{T} <: DistributedFactorGraphs.AbstractManifoldMinimize
```

これはレーダーアライメントファクターがどのように機能するかの一つの具現化に過ぎず、出発点として扱ってください。

ノート

  * 標準の `cvt` 引数は、受信した画像をユーザーの画像軸の慣習に変換するためのラムダ関数です。

      * デフォルトの `cvt` は画像の行を反転させ、Pose2のxy軸がimg[x,y]に対応するようにします。つまり、左上隅から下に行き、横に進みます。
  * 受信した画像の解像度を下げるためにリサイズするには、rescaleを使用します（より速い相関のため）。
  * 構築に渡される両方の画像は、型 `T` の同じタイプの行列でなければなりません。

## 例

```julia
arp2 = ScanMatcherPose2(img1, img2, 2) # 例: 2メートル/ピクセル 
```

参照: [`overlayScanMatcher`](@ref)
