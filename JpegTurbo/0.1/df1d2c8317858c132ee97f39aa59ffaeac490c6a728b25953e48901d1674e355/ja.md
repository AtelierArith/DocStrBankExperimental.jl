```
jpeg_encode(filename::AbstractString, img; kwargs...) -> Int
jpeg_encode(io::IO, img; kwargs...) -> Int
jpeg_encode(img; kwargs...) -> Vector{UInt8}
```

2D画像`img`をJPEGバイトシーケンスとしてエンコードし、指定されたI/Oストリームまたはファイルに書き込みます。戻り値はバイト数です。出力が指定されていない場合、エンコードされた結果はメモリに保存され、戻り値として返されます。

# パラメータ

  * `transpose::Bool`: エンコードする前に画像の幅と高さの次元を入れ替える必要があるかどうか。デフォルト値は`false`です。
  * `quality::Int`: 指定された品質設定に適したJPEG量子化テーブルを構築します。品質値はIJGによって推奨される0..100スケールで表現されます。デフォルト値は`92`です。`quality=nothing`を渡すと、libjpeg-turboが動的に値を推測します。

!!! info "カスタム圧縮パラメータ"
    JPEGには、画像がどのようにエンコードされるかを決定する多くの圧縮パラメータがあります。ほとんどのアプリケーションは、これらのすべてのパラメータについて知る必要はありません。詳細な情報と説明については、[1]の「圧縮パラメータの選択」を参照してください。サポートされていないカスタムパラメータは、Juliaのセグメンテーションフォルトを引き起こす可能性があります。


# 例

```jldoctest
julia> using JpegTurbo, TestImages

julia> img = testimage("cameraman");

julia> jpeg_encode("out.jpg", img) # ファイルに書き込む
51396

julia> buf = jpeg_encode(img); length(buf) # メモリに直接書き込む
51396
```

# 参考文献

  * [1] [libjpeg API Documentation (libjpeg.txt)](https://raw.githubusercontent.com/libjpeg-turbo/libjpeg-turbo/main/libjpeg.txt)

```
