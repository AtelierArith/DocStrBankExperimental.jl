```
generate_io_validator(funcname::Symbol, regex::RE; goto::Bool=false)
```

**注意: このメソッドは TranscodingStreams をロードする必要があります**

評価されると、`funcname` という名前の関数を定義するコードを作成します。この関数は `IO` を受け取り、入力内のデータが正規表現に準拠しているかどうかをチェックし、何のアクションも実行しません。入力が準拠している場合は `nothing` を返します。そうでない場合は `(byte, (line, col))` を返します。ここで `byte` は最初の無効なバイトで、`(line, col)` はそのバイトの1-indexed位置です。無効なバイトが `\n` バイトの場合、`col` は 0 になり、行番号がインクリメントされます。入力が予期しない EOF によりエラーが発生した場合、`byte` は `nothing` になり、行と列はファイル内の最後のバイトになります。

`goto` が指定されている場合、関数はより速いがより複雑な `:goto` コードを使用します。

参照: [`generate_buffer_validator`](@ref)
