```
J = imfilter(I::GMTimage, kernel::Matrix{<:Real}; normalize::Int=1, sep::Bool=false)::GMTimage
```

一般的な畳み込みフィルター。

### 引数

  * `I::GMTimage`: 入力画像。これはRGBまたはグレースケール画像である可能性があります。
  * `kernel::Matrix{<:Real}`: フィルターカーネルのMxN行列。

### キーワード引数

  * `normalize::Int=1`: フィルターを単位和に正規化します。これはデフォルトであり、$sum(kernel) == 0$ の場合は0に変更されます。
  * `sep::Bool=false`: フィルターを2つの1次元成分に分解しようとします。可能であれば、これにより実行が速くなります。MxN x (m+n) 操作の代わりに MxN x mxn。ここで、M,Nおよびm,nはそれぞれ画像Iとカーネルフィルターのサイズです。

### 戻り値

フィルター処理された画像を持つ、`I`と同じタイプの新しい`GMTimage`。

### 例

画像 "moon.png" に3x3平均除去フィルターを適用します。

```julia
I = gmtread(TESTSDIR * "assets/moon.png");
J = imfilter(I, [-1 -1 -1; -1 9 -1; -1 -1 -1]);
grdimage(I, figsize=5)
grdimage!(J, figsize=5, xshift=5, show=true)
```
