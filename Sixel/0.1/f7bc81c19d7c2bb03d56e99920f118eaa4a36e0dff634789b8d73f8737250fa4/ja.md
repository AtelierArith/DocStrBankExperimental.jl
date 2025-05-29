```
sixel_encode([io], src, [encoder]; kwargs...)
```

色素シーケンス `src` をシクセルシーケンスとしてエンコードし、書き込み可能な io ライクオブジェクト `io` に書き込みます。

# 引数

  * `io`: 出力 io ライクオブジェクトで、書き込み可能であることが期待されます。一般的な選択肢は: `stdout`, `IOBuffer` および `IOStream` です。デフォルト値は `stdout` です。
  * `src`: 色素シーケンスを含む一般的なコンテナオブジェクト（例: `AbstractArray`）。
  * `encoder::AbstractSixelEncoder`: シクセルエンコーダー。現在利用可能なのは [`LibSixelEncoder`](@ref Sixel.LibSixel.LibSixelEncoder) のみです。

!!! warning
    小さな画像（ベクターを含む）に対する `sixel_encode` は未定義の動作です。シクセル形式は、行方向に少なくとも `6` ピクセルを必要とします。より良い視覚化結果を得るために、データのサイズが両方の次元で `(6, 6)` より大きくなるように `repeat`（内部）することをお勧めします。


!!! note
    `ndims(src) >= 3` の配列の場合、エンコードの前に行順に 2d 配列に連結されます。


# パラメータ

  * `transpose::Bool`: エンコードの前に画像の幅と高さの次元を入れ替える必要があるかどうか。デフォルト値は `false` です。

# 例

```julia
using Sixel, TestImages

# 2d RGB 画像
img = testimage("mandril_color")
sixel_encode(img)

# 3d RGB 画像は行順に連結されます。
img3d = testimage("mri-stack")
sixel_encode(img3d)

# エンコードされたシクセルシーケンスを `IOBuffer` または `IOStream`（`open` 経由）に書き込むこともできます。
io = IOBuffer()
sixel_encode(io, img)
println(String(take!(io)))

open("out.sixel", "w") do io
    sixel_encode(io, img)
end
```

# 参考文献

  * [1] VT330/VT340 プログラマリファレンスマニュアル, ボリューム 1: テキストプログラミング
  * [2] VT330/VT340 プログラマリファレンスマニュアル, ボリューム 2: グラフィックスプログラミング
  * [3] https://github.com/saitoha/libsixel

```
