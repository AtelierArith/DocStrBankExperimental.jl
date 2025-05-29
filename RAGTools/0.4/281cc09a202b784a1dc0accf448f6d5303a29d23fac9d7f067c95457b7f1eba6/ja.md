```
print_html([io::IO,] parent_node::AbstractAnnotatedNode)

print_html([io::IO,] rag::AbstractRAGResult; add_sources::Bool = false,
	add_scores::Bool = false, default_styler = HTMLStyler(),
	low_styler = HTMLStyler(styles = "color:magenta", classes = ""),
	medium_styler = HTMLStyler(styles = "color:blue", classes = ""),
	high_styler = HTMLStyler(styles = "", classes = ""), styler_kwargs...)
```

注釈 `parent_node`（または `RAGResult`）を `io` ストリームに HTML 形式でプリントします（または文字列を返します）（ノードがスタイラー `HTMLStyler` でスタイリングされていると仮定します）。

各「トークン」を要求されたスタイリング（HTMLStyler のプロパティ `classes` と `styles`）を持つ span にラップします。また、より良い HTML フォーマットのために改行を `<br>` に置き換えます。

非 HTML スタイラーの場合、内容をプレーンテキストとして印刷します。

# 戻り値

  * `io` が提供されている場合は `nothing`
  * または HTML 形式のテキストを含む文字列（`io` が提供されていない場合、結果を出力します）

スタイリングがどのように適用され、引数が何を意味するかについては、`HTMLStyler`、`annotate_support`、および `set_node_style!` も参照してください。

# 例

注意: `RT` は `RAGTools` のエイリアスです

`RAGResult` から直接シンプルに始めます：

```julia
# テキスト/RAGResult を設定
context = [
	"This is a test context.", "Another context sentence.", "Final piece of context."]
answer = "This is a test answer. It has multiple sentences."
rag = RT.RAGResult(; context, final_answer=answer, question="")

# HTML を印刷
print_html(rag)
```

私たちの `AnnotatedNode` を作成することで低レベルの制御を行います：

```julia
# HTML スタイリングを準備
styler_kwargs = (;
	default_styler=RT.HTMLStyler(),
	low_styler=RT.HTMLStyler(styles="color:magenta", classes=""),
	medium_styler=RT.HTMLStyler(styles="color:blue", classes=""),
	high_styler=RT.HTMLStyler(styles="", classes=""))

# テキストに注釈を付ける
context = [
	"This is a test context.", "Another context sentence.", "Final piece of context."]
answer = "This is a test answer. It has multiple sentences."

parent_node = RT.annotate_support(
	RT.TrigramAnnotater(), answer, context; add_sources=false, add_scores=false, styler_kwargs...)

# HTML を印刷
print_html(parent_node)

# または、さらにノードを蓄積するために
io = IOBuffer()
print_html(io, parent_node)
```
