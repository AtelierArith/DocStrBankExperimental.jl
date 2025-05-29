```
struct FilePath path::String end
```

Baseに奇妙に欠けているファイルパスタイプの粗い代替物です。

これにより、ロード/ライトメソッドのディスパッチが可能になり、ファイルパスからファイルコンテンツ（Stringとして）を区別できます。

# 例

```julia-repl
julia> string(FilePath("some/path"))
"some/path"
```
