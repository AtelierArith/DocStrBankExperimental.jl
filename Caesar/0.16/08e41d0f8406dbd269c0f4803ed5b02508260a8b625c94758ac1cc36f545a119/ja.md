```julia
struct Pose2AprilTag4Corners{T<:(IncrementalInference.SamplableBelief), F<:Function} <: DistributedFactorGraphs.AbstractManifoldMinimize
```

4つのコーナー検出のAprilTagsからPose2Pose2因子への変換のための簡略化されたコンストラクタタイプ

ノート

  * 座標フレームは：

      * ロボティクスのボディフレームはxyz <==> fwd-lft-upを仮定
      * AprilTagsのポーズはxyz <==> rht-dwn-fwdを仮定
      * カメラフレームはxyz <==> rht-dwn-fwdを仮定
      * Images.jlフレームは行-列 <==> i-j  <==> dwn-rhtを仮定
  * ヘルパーコンストラクタは`f_width, f_height, c_width, c_height,s`を使用して`K`を構築します。

      * `K`を設定すると`f_width,f_height, c_width, c_height,s`が上書きされます。
  * MvNormalの平均の代わりにデコンボリューション測定サンプル`idx`からの前像を見つける：

      * 詳細については[`generateCostAprilTagsPreimageCalib`](@ref)を参照してください。

例

```julia
# パッケージをインポート
using AprilTags, Caesar, FileIO

# タグのサイズ、黒い四角の各辺の外側の長さ
taglength = 0.15

# 画像を読み込む
img = load("photo.jpg")

# 画像のサイズ
width, height = size(img)
# 自動推測 `f_width=height, c_width=round(Int,width/2), c_height=round(Int, height/2)`

detector = AprilTagDetector()
tags = detector(img)

# Pose2 `:x0`とPriorを持つ新しい因子グラフ
fg = generateGraph_ZeroPose(varType=Pose2)

# すべてのタグに因子を追加するための構築ヘルパーを使用
for tag in tags
  tagSym = Symbol("tag$(tag.id)")
  exists(fg, tagSym) ? nothing : addVariable!(fg, tagSym, Pose2)
  pat = Pose2AprilTag4Corners(corners=tag.p, homography=tag.H, taglength=taglength)
  addFactor!(fg, [:x0; tagSym], pat)
end

# AprilTagsライブラリのメモリを解放
freeDetector!(detector)
```

DevNotes

  * TODO IIFは、単一のキャリブレーション検索に多くの前像`obj`項を組み合わせるための配管を取得します

関連

`AprilTags.detect`, `PackedPose2AprilTag4Corners`, [`generateCostAprilTagsPreimageCalib`](@ref)
