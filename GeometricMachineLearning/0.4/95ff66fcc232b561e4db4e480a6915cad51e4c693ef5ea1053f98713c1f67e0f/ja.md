```
DataLoader(data::AbstractArray{T, 3}, target::AbstractVector)
```

分類問題のためのDataLoaderのインスタンスを作成します。

ここでのターゲットはラベルのベクトルです。これは、パッケージ[`MLDatasets.jl`](https://github.com/JuliaML/MLDatasets.jl)で使用するように調整されています。

# 引数

2つのキーワード引数があります：

  * `patch_length = 7`。これは$x$および$y$方向のパッチの長さです；
  * `suppress_info = false`。

MNISTデータセットの例では、すべての画像は$49\times49$のサイズです。`patch_length = 7`の場合、画像はしたがって16の$7\times7$パッチに分割されます[brantner2023generalizing](@cite)。
