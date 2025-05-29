```
OutputOptions(;
    code_class::AbstractString="language-julia",
    output_pre_class::AbstractString="code-output documenter-example-output",
    hide_code::Bool=false,
    hide_md_code::Bool=true,
    hide_md_def_code::Bool=true,
    add_state::Bool=true,
    append_build_context::Bool=false,
    show_output_above_code::Bool=false,
    replace_code_tabs::Bool=true,
    convert_admonitions::Bool=true
)
```

引数:

  * `code_class`:   コードのためのHTMLクラス。   これはCSSおよび/または構文ハイライターによって使用されます。
  * `output_pre_class`:   `<pre>`のためのHTMLクラス。
  * `output_class`:   出力のためのHTMLクラス。   これはCSSおよび/または構文ハイライターによって使用されます。
  * `hide_code`:   すべてのコードブロックを省略するかどうか。   読者がコードに全く興味がない場合に便利です。
  * `hide_md_code`:   すべてのMarkdownコードブロックを省略するかどうか。
  * `hide_md_def_code`:   Franklin Markdown定義コードブロック（+++で囲まれたブロック）を省略するかどうか。
  * `add_state`:   入力ノートブックの状態をHTMLのコメントとして追加するかどうか。   この状態はキャッシングに使用できます。   特に、この状態は入力ノートブックのチェックサムとJuliaのバージョンを保存します。
  * `append_build_context`:   ビルドコンテキストを追加するかどうか。   `true`に設定すると、依存関係とJuliaのバージョンに関する情報が追加されます。   これは、既存のノートブックに追加の依存関係を追加する必要がないように、Pluto.jlの評価を介して実行されません。   代わりに、これはノートブックファイルからマニフェストを読み取ります。
  * `show_output_above_code`:   コードの上にコードからの出力を表示するかどうか。   Pluto.jlはデフォルトでコードの上に出力を表示します; このパッケージはデフォルトでコードの下に出力を表示します。   コードの上に出力を表示するには、`show_output_above_code=true`を設定します。
  * `replace_code_tabs`:   コードブロック内の行の先頭にあるタブをスペースに置き換えます。   これにより、ウェブページ上のコードブロックの外観が不一致になるのを避けます。
  * `convert_admonitions`:   `!!! note       これはノートです。`   のような注意書きをPlutoのHTMLからDocumenterのHTMLに変換します。   これが有効な場合、`documenter_output`はデフォルトで適切なスタイリングを持ちます。
