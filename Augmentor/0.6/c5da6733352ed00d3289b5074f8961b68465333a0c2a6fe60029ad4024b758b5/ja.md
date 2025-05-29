```
augmentbatch!([resource], outs, imgs, pipeline, [obsdim]) -> outs
```

与えられた `pipeline` の操作を `imgs` の画像に適用し、結果の画像を `outs` に書き込みます。

`outs` と `imgs` は同じ数の画像を含む必要があります。これらの2つの変数は、より高次元の配列の形、または各ベクトル要素が画像を示す配列のベクトルの形をとることができます。

```julia
# サイズ3x3の5つの例の観測を作成
imgs = rand(3,3,5)
# 適切な形の出力配列を作成
outs = similar(imgs)
# 画像のバッチを変換
augmentbatch!(outs, imgs, FlipX() |> FlipY())
```

2つのパラメータ `outs` と `imgs` のうちの1つ（または両方）が高次元の配列である場合、オプションのパラメータ `obsdim` を使用して観測を示す次元を指定できます（デフォルトは `ObsDim.Last()`）。

```julia
# サイズ3x3の5つの例の観測を作成
imgs = rand(5,3,3)
# 適切な形の出力配列を作成
outs = similar(imgs)
# 画像のバッチを変換
augmentbatch!(outs, imgs, FlipX() |> FlipY(), ObsDim.First())
```

[`augment!`](@ref) と同様に、`outs` と `imgs` の両方が同じ長さのタプルであることも許可されています。その場合、各タプル要素は上記のいずれかの形をとることができます。これは、各観測が複数の画像で構成される画像セグメンテーションなどのタスクに便利です。

```julia
# 各観測が概念的に関連する2つの3x3配列で構成される5つの例の観測を作成
imgs = (rand(3,3,5), rand(3,3,5))
# 適切な形の出力配列を作成
outs = similar.(imgs)
# 画像のバッチを変換
augmentbatch!(outs, imgs, FlipX() |> FlipY())
```

パラメータ `pipeline` は `Augmentor.Pipeline`、`Augmentor.Operation` のタプル、または単一の `Augmentor.Operation` であることができます。

```julia
augmentbatch!(outs, imgs, FlipX() |> FlipY())
augmentbatch!(outs, imgs, (FlipX(), FlipY()))
augmentbatch!(outs, imgs, FlipX())
```

オプションの最初のパラメータ `resource` は `CPU1()`（デフォルト）または `CPUThreads()` であることができます。後者の場合、画像は並列に拡張されます。これが意味を持つためには、環境変数 `JULIA_NUM_THREADS` が適切な数に設定されていることを確認し、`Threads.nthreads()` が1より大きいことを確認してください。

```julia
# マルチスレッドを使用して画像のバッチを並列に変換
augmentbatch!(CPUThreads(), outs, imgs, FlipX() |> FlipY())
```
