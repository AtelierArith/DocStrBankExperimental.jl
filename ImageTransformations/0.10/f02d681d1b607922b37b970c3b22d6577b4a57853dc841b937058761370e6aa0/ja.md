このパッケージは、画像のリサイズ、画像の回転、および配列の他の空間変換をサポートします。

  * `WarpedView`: `img`のビューを作成し、`wv[I]`に渡された任意のインデックス`I`を遅延変換して、`wv[I] == img[tform(I)]`となるようにします。
  * `warp`: `WarpedView`の即時評価バリアント。`img`の座標を変換し、`imgw`を返して`imgw[I] = img[tform(I)]`を満たします。
  * `InvWarpedView`: `img`のビューを作成し、`wv[I]`に渡された任意のインデックス`I`を遅延変換して、`wv[I] == img[inv(tinv)(I)]`となるようにします。
  * `imresize`: 補間を使用して、画像`img`を指定されたサイズ`sz`または軸`inds`にアップサンプリング/ダウンサンプリングします。
  * `restrict`: 画像を1/2サイズに近似するために二重にダウンサンプリングする、`imresize`のはるかに効率的なバージョンです。（これは現在`ImageBase.restrict`によって提供されています）
  * `imrotate`: 画像`img`を中心点の周りで時計回りに`θ`∈[0,2π)だけ回転させます。
  * `autorange`: 与えられた変換`tform`に対して、`tform`を適用した後に`A`からのすべての情報を保持する「最小」範囲インデックスを返します。

多くの関数にはインプレースバージョンがあり、例えば`imresize!`などがあります。

リサイズの例:

```julia
using ImageTransformations, TestImages

img = testimage("mandrill")

img_small = imresize(img, ratio=1/8)
img_medium = imresize(img_small, size(img_small).*2)
```

ワーピングの例:

```julia
using ImageTransformations, TestImages, CoordinateTransformations, Rotations

img = testimage("camera");

# 変換を定義
trfm = recenter(RotMatrix(pi/8), center(img));
imgw = warp(img, trfm);
```
