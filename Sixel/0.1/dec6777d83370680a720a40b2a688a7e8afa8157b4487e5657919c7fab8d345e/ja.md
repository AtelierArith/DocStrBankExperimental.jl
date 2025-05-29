```
sixel_decode([T=RGB{N0f8}], src, [decoder]; kwargs...) -> img::IndirectArray
```

`sixel_decode`関数は、`src`で提供されたsixel形式のシーケンスをデコードし、インデックス付き画像として出力します。

# 引数

  * `T`: 出力のeltype。デフォルトは`RGB{N0f8}`です。
  * `src`: 入力sixelデータソース。`IO`、`AbstractVector{UInt8}`、または`AbstractString`のいずれかです。
  * `decoder::AbstractSixelDecoder`: sixelデコーダー。現在利用可能なのは`LibSixelDecoder`のみです。

!!! warning
    小さな画像（ベクターを含む）に対する`sixel_decode`は未定義の動作です。sixel形式は、行方向に少なくとも`6`ピクセルを必要とします。たとえば、たとえそれが`Vector`データを返すことを期待しないでください。


# パラメータ

  * `transpose::Bool`: エンコードする前に画像の幅と高さの次元を入れ替える必要があるかどうか。デフォルト値は`false`です。

# 参考文献

  * [1] VT330/VT340 プログラマリファレンスマニュアル、第1巻: テキストプログラミング
  * [2] VT330/VT340 プログラマリファレンスマニュアル、第2巻: グラフィックスプログラミング
  * [3] https://github.com/saitoha/libsixel

```
