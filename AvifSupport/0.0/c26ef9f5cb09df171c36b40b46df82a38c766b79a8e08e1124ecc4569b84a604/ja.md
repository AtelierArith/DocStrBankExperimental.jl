```
avif_decode(filename::Union{AbstractString,IO}; kwargs...) -> Vector{Matrix{Colorant}}
avif_decode(data::Vector{UInt8}; kwargs...) -> Vector{Matrix{Colorant}}
```

AVIF画像をカラーマトリックスの配列としてデコードします。ソースデータは、ファイル名、IO、またはメモリ内のバイトシーケンスのいずれかです。出力は`Colorant`型のマトリックスの配列です。

# パラメータ

  * `transpose::Bool`: エンコードする前に画像の幅と高さの次元を入れ替える必要があるかどうか。デフォルト値は`false`です。

    !!! info "カスタムデコードパラメータ"

```
LibAvifには、画像がどのようにデコードされるかを決定する多くのデコーダーパラメータがあります。ほとんどのアプリケーションは、これらすべてのパラメータについて知る必要はありません。詳細な情報と説明については、[1]の文書を参照してください。サポートされていないカスタムパラメータは、Juliaのセグメンテーションフォルトを引き起こす可能性があります。

この実装でデコードに使用されるデフォルトのパラメータは次のとおりです：

  * codecChoice = libaom
  * maxThreads = Threads.nthreads()
  * speed = 4
```

# 参考文献

  * [1] [libavif avifdec.c ](https://github.com/AOMediaCodec/libavif/blob/main/apps/avifdec.c)
