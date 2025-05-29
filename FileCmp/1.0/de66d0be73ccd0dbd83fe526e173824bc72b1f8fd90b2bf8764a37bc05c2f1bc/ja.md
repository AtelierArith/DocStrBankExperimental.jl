```
filecmp(path1::AbstractString, path2::AbstractString, bufsize=0; info=Val(false); limit=0)
filecmp(io1::IO, io2::IO, bufsize=0; info=Val(false), limit=0)
```

`path1` と `path2` のファイルが同じ内容を持っているかどうかを判断し、オプションでどのように異なるかの情報を返します。`info==false` の場合、戻り値の型は `Bool` です。この場合、`path1` と `path2` のファイルがバイト単位で等しい場合は `true` を、そうでない場合は `false` を返します。

`info==true` の場合、戻り値の型は `FileCmp.Info` で、ファイルが異なる場合のバイトインデックスとファイルのサイズの比較を記録します。（[`FileCmp.Info`](@ref) を参照）。結果は `files_equal`、`got_eof`、および `bytes_read` 関数で照会できます。

`path1` または `path2` が存在しない場合、例外がスローされます。

キーワード引数 `info` は `true`、`false`、`Val(true)`、または `Val(false)` のいずれかである必要があります。最初の2つはより便利です。後の2つは戻り値の型を推論できるようにします。

`limit` がゼロより大きい場合、最大で `limit` バイトを読み取ります。

ファイルは `bufsize` バイトのバッファに読み込まれます。`bufsize=0` の場合、デフォルトが使用されます。

# 例

最も簡単な使い方

```julia
using FileCmp
filecmp("file1", "file2")  # `true` または `false` を返す
```

より多くの情報を得るには、次のようにします

```julia
using FileCmp: filecmp, bytes_read, got_eof, files_equal
info_result = filecmp("file1", "file2"; info=true)
bytes_read(info_result) # 読み取ったバイト数
got_eof(info_result) # ファイルで eof に達しましたか？ (got_eof のドキュメントを参照)
files_equal(info_result) # ファイルは等しいですか？
```
