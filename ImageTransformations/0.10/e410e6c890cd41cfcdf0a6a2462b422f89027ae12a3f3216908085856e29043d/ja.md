```
imresize(img, sz; [method]) -> imgr
imresize(img, inds; [method]) -> imgr
imresize(img; ratio, [method]) -> imgr
```

画像 `img` を指定されたサイズ `sz` または軸 `inds` にアップサンプル/ダウンサンプルします。`ratio` が提供されると、出力サイズは `ceil(Int, size(img).*ratio)` になります。

!!! tip
    これはサブピクセル位置での値を補間します。画像を縮小する場合、最初に `img` をローパスフィルタリングしないとエイリアシングのリスクがあります。


# 引数

  * `img`: 入力画像配列
  * `sz`: 出力配列のサイズ
  * `inds`: 出力配列の軸 `inds` が渡されると、出力配列 `imgr` は `OffsetArray` になります。

# パラメータ

!!! info
    `method` を構築するには、最初に `Interpolations` パッケージをロードする必要があります。


  * `ratio`: 使用されるアップサンプル/ダウンサンプル比率。出力サイズは `ceil(Int, size(img).*ratio)` です。`ratio` が `1` より大きい場合、アップサンプル操作です。そうでなければダウンサンプル操作です。`ratio` はタプルでもあり、その場合 `ratio[i]` は次元 `i` でのリサイズ比率を指定します。
  * `method::InterpolationType`: 再構築に使用される補間方法を指定します。便利なことに、`method` は `Degree` 型でもあり、その場合 `BSpline` オブジェクトが作成されます。例えば、`method = Linear()` は `method = BSpline(Linear())` と同等です。

# 例

```julia
using ImageTransformations, TestImages, Interpolations

img = testimage("lighthouse") # 512*768

# サイズとして整数を渡す
imresize(img, 256, 384) # 256*384
imresize(img, (256, 384)) # 256*384
imresize(img, 256) # 256*768

# 軸としてインデックスを渡す
imresize(img, 1:256, 1:384) # 256*384
imresize(img, (1:256, 1:384)) # 256*384
imresize(img, (1:256, )) # 256*768

# リサイズ比率を渡す
imresize(img, ratio = 0.5) #256*384
imresize(img, ratio = (2, 1)) # 1024*768

# 異なる補間方法を使用
imresize(img, (256, 384), method=Linear()) # 256*384 バイリニア補間
imresize(img, (256, 384), method=Lanczos4OpenCV()) # 256*384 OpenCV互換 Lanczos 4 補間
```

`ratio=0.5` でダウンサンプルする場合、[`restrict`](@ref) は使用できるはるかに高速な二重実装です。
