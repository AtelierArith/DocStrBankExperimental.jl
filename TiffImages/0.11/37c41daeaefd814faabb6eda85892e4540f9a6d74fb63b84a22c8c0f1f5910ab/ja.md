```julia
mutable struct TiffFile{O<:Unsigned, S<:FileIO.Stream}
```

-> TiffFile

`io`をヘルパーパラメータでラップして、ファイル属性を追跡します。

  * `uuid`: このファイルの一意の識別子
  * `filepath`: このファイルへの相対パス
  * `io`: ファイルストリーム
  * `first_offset`: ファイルストリーム内の最初のIFDの位置
  * `need_bswap`: このファイルがホストコンピュータとは異なるエンディアンを持つかどうか
