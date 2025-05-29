```
@g_str
```

`g"content"`と入力することでGAP文字列を作成します。

# 例

```jldoctest
julia> g"foo"
GAP: "foo"

julia> g"ab\ncd\"ef\\gh"   # 特殊文字はGAPと同様に処理されます
GAP: "ab\ncd\"ef\\gh"

```

Juliaのマクロに引数を渡す方法のため、すべての有効なGAP文字列を表す文字列が処理できるわけではありません。

```jldoctest
julia> g"\\"
ERROR: GAPによってスローされたエラー: 構文エラー: 文字列はファイルの終わりの前に " で終わる必要があります:1
[...]

```

逆に、マクロの有効な引数であっても、有効なJulia文字列ではないものがあります。

```jldoctest
julia> g"\c"
GAP: "\c"

```
