```julia
mutable struct Writer{A, FL, var"356", var"357", var"358", Symbol, var"359", var"366", Int, var"367", var"368", var"369", var"370"} <: Causal.AbstractSink
```

`Writer`を構築し、その入力バスは`input`です。`buflen`は`Writer`の内部バッファの長さです。`plugin`が`nothing`でない場合、受信データを処理するために使用されます。`path`は`Writer`のファイルのパスを決定します。

# フィールド

  * `action::Any`: データをファイルに書き込むためのWriterアクション
  * `path::String`: Writerのファイルパス
  * `file::Any`: データが記録されるファイル
  * `trigger::Any`
  * `handshake::Any`
  * `callbacks::Any`
  * `name::Any`
  * `id::Any`
  * `input::Any`
  * `buflen::Any`
  * `plugin::Any`
  * `timebuf::Any`
  * `databuf::Any`
  * `sinkcallback::Any`

!!! note
    `Writer`の`file`の型は[`JLD2`](https://github.com/JuliaIO/JLD2.jl)です。


!!! warning
    初期化時、`Writer`の`file`は閉じられています。[`open(writer::Writer)`](@ref)および[`close(writer::Writer)`](@ref)を参照してください。

