```
avif_encode(image::AbstractMatrix{TColor}) -> Vector{UInt8}
avif_encode(image_arr::AbstractArray) -> Vector{UInt8}
```

2D画像`img`または2D画像の配列`image_arr`をAVIFバイトシーケンスとしてエンコードします。戻り値はバイトのベクターです。

# avif_encode(image::AbstractMatrix{TColor})のパラメータ

  * `transpose::Bool`: エンコードする前に画像の幅と高さの次元を入れ替える必要があるかどうか。デフォルト値は`false`です。
  * `quality::Int`: 品質値は0..100の範囲です。デフォルト値は`10`です。

      * `transpose::Bool`: エンコードする前に画像の幅と高さの次元を入れ替える必要があるかどうか。デフォルト値は`false`です。
  * `mode::String`: 入力画像のエンコードタイプを決定します。2D画像の場合、エンコードモードは2つの値のいずれかです：デフォルトの`"one_frame"`と`"grid"`です。

    # avif*encode(image*arr::AbstractArray)のパラメータ

      * `transpose::Bool`: エンコードする前に画像の幅と高さの次元を入れ替える必要があるかどうか。デフォルト値は`false`です。
      * `quality::Int`: 品質値は0..100の範囲です。デフォルト値は`10`です。
      * `mode::String`: 入力のエンコードタイプを決定します。2D画像の配列の場合、エンコードモードは3つの値のいずれかです：デフォルトの`"seq"`（順次）、`"grid"`または`"layered"`です。
      * `grid_cols::Int`: - グリッドエンコーディングにのみ関連 - 結果の画像の列数を決定します。grid_colsの値は入力ベクターの長さに依存します。デフォルト値は`1`です。
      * `grid_rows::Int`: - グリッドエンコーディングにのみ関連 - 結果の画像の行数を決定します。grid_rowsの値は入力ベクターの長さに依存します。デフォルト値は`1`です。
      * `timescale::Int`: - レイヤーエンコーディングにのみ関連 - デフォルト値は`1`です。

!!! info "カスタムエンコーディングパラメータ"
    LibAvifには、画像がどのようにエンコードされるかを決定する多数のエンコーダーパラメータがあります。ほとんどのアプリケーションは、これらのすべてのパラメータについて知る必要はありません。詳細な情報と説明については、ドキュメント[1]を参照してください。サポートされていないカスタムパラメータは、Juliaのセグメンテーションフォルトを引き起こす可能性があります。

    この実装でデコードに使用されるデフォルトのパラメータは次のとおりです：

      * codecChoice = libaom
      * maxThreads = Threads.nthreads()
      * speed = 4


!!! danger "グリッドエンコーディングについて"
    ```
    grid_cols * grid_rows = length(image_arr)
    ```


# 参考文献

  * [1] [libavif avifenc.c ](https://github.com/AOMediaCodec/libavif/blob/main/apps/avifenc.c)
