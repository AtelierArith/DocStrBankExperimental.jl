```
TranscodingStream(codec::Codec, stream::IO;
                  bufsize::Integer=16384,
                  stop_on_end::Bool=false,
                  sharedbuf::Bool=(stream isa TranscodingStream))
```

`codec` と `stream` を使用してトランスコーディングストリームを作成します。

`TranscodingStream` オブジェクトは、入力/出力ストリームオブジェクト `stream` をラップし、`codec` を使用してバイトストリームをトランスコードします。これは `IO` のサブタイプであり、標準ライブラリのほとんどの I/O 関数をサポートしています。

利用可能なコーデック、例、および型の詳細については、ドキュメントを参照してください ([https://bicycle1885.github.io/TranscodingStreams.jl/stable/](https://bicycle1885.github.io/TranscodingStreams.jl/stable/))。

## 引数

  * `codec`:   データトランスコーダー。トランスコーディングストリームは `codec` の初期化と最終化を行います。したがって、コーデックオブジェクトはトランスコーディングストリームに渡されると再利用できません。
  * `stream`:   ラップされたストリーム。コンストラクタに渡す前に開いておく必要があります。
  * `bufsize`:   初期バッファサイズ（デフォルトサイズは 16KiB）。`codec` が要求するたびにバッファは拡張される可能性があります。
  * `stop_on_end`:   `codec` からの `:end` リターンコードで読み取りを停止するフラグ。トランスコーディングプロセスを停止した後でも、トランスコードされたデータは読み取ることができます。このフラグがオンの場合、ラッパーストリームが `close` で閉じられても `stream` は閉じられません。ストリームから追加のデータが内部バッファに読み込まれる可能性があるため、`stream` は `TranscodingStream` オブジェクトであり、`sharedbuf` は `true` である必要があります。
  * `sharedbuf`:   隣接するトランスコーディングストリーム間でバッファを共有するフラグ。`stream` が `TranscodingStream` オブジェクトでない場合、値は `false` でなければなりません。

## 例

```jldoctest
julia> using TranscodingStreams

julia> file = open(joinpath(dirname(dirname(pathof(TranscodingStreams))), "README.md"));

julia> stream = TranscodingStream(Noop(), file);

julia> readline(file)
"TranscodingStreams.jl"

julia> close(stream)
```
