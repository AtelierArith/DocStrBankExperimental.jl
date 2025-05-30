```
ShowList
```

`AbstractShow` のラッパータイプで、イテラブルを表示します。 `ShowCases` モジュールは主に Julia 構文に似た出力を持つ `show` メソッドを作成することを目的としているため、すべてのイテラブルはランク 1 のものとして表示されます。より高いランクの配列は、組み込みメソッドやそれらを処理するために特に意図されたツールを使用して表示する必要があります。

`ShowList` は、`ShowEntry` オブジェクトである任意の要素をそのまま表示します。したがって、特定のエントリのデフォルトをオーバーライドするために `ShowEntry` オブジェクトを渡すことができます。

## コンストラクタ

  * `ShowList(o; brackets="()", left_bracket=Print("("), right_bracket=Print(")"),           new_lines=false, indent="    ", delim=Print(", "), max=8,           continuation=Print("…"), entry_style=nothing)`
  * `ShowList(o...; kw...)` （上記と同じキーワード引数）

## 引数

  * `o`: ラップするオブジェクトまたはオブジェクト。 1 つだけ渡される場合、それはイテラブルでなければなりません。
  * `brackets`: 使用するブラケットを含む文字列（例: `"()", "[]", "{}", "''"`）
  * `left_bracket`: 表示される左ブラケット。 デフォルトでは、これは `brackets` から計算されます。 引数が直接与えられた場合、それはそのまま表示されます。つまり、引用符を省略するには `Print("(")` を使用します。
  * `right_bracket`: 表示される右ブラケット。 デフォルトでは、これは `brackets` から計算されます。 引数が直接与えられた場合、それはそのまま表示されます。つまり、引用符を省略するには `Print(")")` を使用します。
  * `new_lines::Bool`: 各エントリのために新しい行を印刷するかどうか。
  * `indent::AbstractString`: 使用するインデント
  * `delim`: 各エントリに使用する区切り文字。 これはそのまま印刷されるため、例えば、スペース付きのカンマを得るには `Print(", ")` を使用します。
  * `max::Integer`: 印刷される最大エントリ数。
  * `continuation`: `max` に達したときに印刷するオブジェクト。 これはそのまま表示されます。

## 例

```
julia> ShowList(1, 2)
(1, 2)

julia> ShowList(1, 2, new_lines=true)
(
    1,
    2
)

julia> ShowList(1, 2, max=1)
(1, …)

# `ShowList` によって設定されたデフォルトをオーバーライドするために ShowEntry オブジェクトを渡す
julia> ShowList(ShowEntry("a", delim=Print(": "), new_line=true), 1, 2)
(
    "a": 1, 2)

```
