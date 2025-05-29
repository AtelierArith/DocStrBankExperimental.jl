生成されたコードで使用される変数名を格納するために使用される構造体。`CodeGenContext`に含まれています。Automaのコード生成で使用される変数をカスタマイズしたい場合、特に同じ名前の競合する変数がある場合は、カスタム`Variables`を作成してください。

Automaは、以下の変数を使用してコードを生成します。デフォルト名とともに示されています：

  * `p::Int`: データの現在の位置
  * `p_end::Int`: データの終了位置
  * `is_eof::Bool`: `p_end`がファイルストリームの終わりを示すかどうか
  * `cs::Int`: 現在の状態
  * `data::Any`: 入力データ
  * `mem::SizedMemory`: `data`をラップするメモリ
  * `byte::UInt8`: `data`から読み取られている現在のバイト
  * `buffer::TranscodingStreams.Buffer`: （`generate_reader`のみ）

# 例

```julia
julia> ctx = CodeGenContext(vars=Variables(byte=:u8));

julia> ctx.vars.byte
:u8
```
