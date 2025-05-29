```
abstract type CustomTextCell
```

テキストバックエンドにおけるカスタムセルの抽象型。

各タイプは以下のAPIを実装する必要があります：

  * `get_printable_cell_text`: 印刷可能なテキストを含む文字列のベクターを返す必要がある関数。すなわち、非印刷可能な文字を含まない。
  * `get_rendered_line`: 表示に印刷されるレンダリングされた行を返す必要がある関数。
  * `apply_line_padding!`: 特定の行の左側と右側に一定数のスペースを適用します。
  * `crop_line!`: 行の末尾から一定数の印刷可能な文字を切り取る必要がある関数。
  * `append_suffix_to_line!`: カスタムセルの行に文字列のサフィックスを追加します。
  * `apply_line_padding!`: カスタムセルの行に左側と右側のパディングを適用します。
  * `crop_line!`: カスタムセルの行から一定数の文字を切り取ります。
  * `get_printable_cell_line`: カスタムセルの印刷可能な行を取得します。
  * `get_rendered_line`: カスタムセルのレンダリングされた行を取得します。
  * `parse_cell_text`: セルテキストを解析し、印刷可能な行を含む `Vector{String}` を返します。
  * `reset!`: すべての一時フィールドをリセットします。この関数は必須ではありません。
