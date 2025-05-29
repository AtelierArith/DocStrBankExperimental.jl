```julia
calcCalibResidualAprilTags!(
    images,
    allTags;
    tagList,
    taglength,
    VERT,
    HORI,
    f_width,
    f_height,
    c_width,
    c_height,
    s,
    boardPattern,
    dodraw
)

```

AprilTagsキャリブレーション補助関数のグリッド。この関数は、`Optim.opimize`を含む任意の方法によって最小化されるべき平方コストを設定します。コスト関数は、40個のAprilTagsが同じサイズで共通の共平面上の表面（コンピュータの画面など）にあると仮定して構築されます。

コスト関数は、各タグ検出から個別に予測し、他の39個のタグのすべてのコーナーが共平面上のどこにあるべきかを予測することによって構築されます。予測されたタグ位置と検出されたタグ位置の間の不一致は、二乗累積されます。

### 注意事項

  * 40個のAprilTagsの規則的な間隔のグリッドを仮定します 36h11, ids=1:40、

      * 1:5の下に8列1:5:40の間隔で、taglengthと間隔が等しい。
      * AprilTags/data/CameraCalibration/AprilTagGrid1to40.pngのグリッドファイルを参照してください。
  * 現在の実装では、すべての40個のタグが可視で検出される必要があります。

      * いくつかの検出漏れを許可するための貢献を歓迎します。
  * キャリブレーションしたいカメラでグリッドの写真を撮影し、すべてのタグが明確に見えるようにしてください。

      * グリッドが近くおよび遠く、視野の端の周りで中心に傾いている組み合わせが最適です。
      * 任意の数の画像を使用できますが、多いほど良いです。
      * 高解像度の画像が半ダースあると、最適化に約20分かかる場合があります。
  * Julia Images.jlは一般的な``::Array`列優先–すなわち垂直優先–インデックス規則に従います。

      * すなわち`img[vertical, horizontal]`
      * https://evizero.github.io/Augmentor.jl/images/#Vertical-Major-vs-Horizontal-Major-1を参照してください。
  * この関数には、予測されたタグのコーナーを描画する機能があります。キーワード`dodraw=true`を参照してください。
  * これは他のAprilCalやそのようなソフトウェアのコピーではなく、動作させるための純粋なフラストレーションから新たに書かれたコードです。よりネイティブなJuliaコードが望ましいです。なぜなら、Juliaは他のキャリブレーションソフトウェアよりもはるかにモバイルで多用途だからです。追加する機能のロードマップについてはDevNotesを参照してください。貢献を歓迎します。

### 例

`AprilTags/examples/AprilTagsGridClibration.jl`も参照してください。

この例では、タググリッド画像の一連の写真（プロジェクターではなくコンピュータの画面を使用）を使用してカメラをキャリブレーションする方法を示しています。この例では基本的なピンホールパラメータのみを示していますが、他にも可能なものがあります。どのキャリブレーションパラメータが利用可能かはキーワード引数を参照してください。後半では、結果の前後を確認するために十字を描画する方法を示しています。

```julia
using AprilTags
using FileIO

# キャリブレーションファイルの写真はどこにありますか
filepaths = ["photo1.jpg"; "photo2.jpg";...]
# 画像をメモリにロード
imgs = load.(filepaths)

# ここでタグの長さを正しく測定し指定することが重要です
# 30 mmは単なる推測です。ここに自分の正しいタグの測定値を挿入してください。
taglength = 0.03

# キャリブレーションパラメータの粗い推測
# img[rows,columns] <==> img[height, width]
c_width = size(imgs[1],2) / 2 # Images.jlの列数
c_height = size(imgs[1],1) / 2 # Images.jlの行数
f_width = size(imgs[1],1)
f_height=f_width

# タグを検出し、検出器を解放する前にメモリを複製
detector = AprilTagDetector()
tags = detector.(imgs) .|> deepcopy
# 後で検出器を解放することを忘れないでください

# コスト関数を設定します。ここにさらにパラメータを追加できます。
obj = (f_width, f_height, c_width, c_height) -> calcCalibResidualAprilTags!( imgs, tags, taglength=taglength, f_width=f_width, f_height=f_height, c_width=c_width, c_height=c_height, dodraw=false )
obj_ = (fc_wh) -> obj(fc_wh...)

# 動作することを確認します
obj_([f_width, f_height, c_width, c_height])

## Optim.jl最適化ルーチンを取り入れます
using Optim

# 最適化を実行します。BFGSは遅いですが、より正確です。粗い最適化段階と細かい最適化段階を混ぜるのは問題ありません。
result = optimize(obj_, [f_width; f_height; c_width; c_height], BFGS(), Optim.Options(x_tol=1e-8))

# 最適化されたキャリブレーションパラメータを確認します
@show f_width_, f_height_, c_width_, c_height_ = (result.minimizer...,)

## 画像の前後を表示して、動作していることを視覚的に確認します
using ImageView

# 悪いキャリブレーション
img1_before = deepcopy(imgs[1])
calcCornerProjectionsAprilTags!(img1_before, taglength=taglength, f_width=f_width, f_height=f_height, c_width=c_width, c_height=c_height, dodraw=true)
imshow(img1_before)

# 新しいキャリブレーション
img1_after = deepcopy(imgs[1])
calcCornerProjectionsAprilTags!(img1_after, taglength=taglength, f_width=f_width_, f_height=f_height_, c_width=c_width_, c_height=c_height_, dodraw=true)
imshow(img1_after)

# 検出器メモリを解放します
freeDetector!(detector) # メモリを二次的な場所に複製し、すぐにプライマリを解放するためにdeepcopyを使用することもできます
```

### DevNotes

  * FIXME 共通のJuliaRobotics/CameraModels.jlパッケージを作成する必要があります
  * TODO 放射歪みパラメータを追加する必要があります。https://en.wikipedia.org/wiki/Distortion_(optics)を参照してください
  * TODO 40個のタグのグリッドでの検出漏れを許可する必要があります
  * TODO どのグリッドでも使用できるようにグリッドを自動検出する必要があります（まだ規則的な間隔を仮定しています）

### 関連

[`calcCornerProjectionsAprilTags!`](@ref)
