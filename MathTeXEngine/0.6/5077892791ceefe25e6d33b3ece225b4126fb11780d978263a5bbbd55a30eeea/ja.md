```
FontFamily(fonts ; font_mapping, font_modifiers, special_chars, slant_angle, thickness)
```

LaTeXレンダリング用のフォントセット。

# 必須フィールド

  * `fonts` 5つのフォントへのパスを持つ配列（:regular, :italic, :bold, :bolditalic, および :math）。同じフォントを複数のエントリで使用することができ、無関係なフォントを混ぜることもできます。

# オプションフィールド

  * `font_mapping` 異なる文字タイプ（`:digit`, `:function`, `:punctuation`, `:symbol`, `:variable`）をフォント識別子にマッピングする辞書。デフォルトは `MathTeXEngine._default_font_mapping`
  * `font_modifiers` フォントセットでサポートされているフォントコマンドごとに1つのエントリを持つ辞書の辞書。各エントリはフォント識別子を別のものにマッピングする辞書です。デフォルトは `MathTeXEngine._default_font_modifiers`。
  * `specail_chars` デフォルトのUnicodeグリフで表現されるべきでない特殊文字のマッピング（例えば、大きな積分グリフにアクセスするために必要）。
  * `slant_angle` イタリックフォントが傾く角度（度）。
  * `thickness` フォントに関連付けられた線の太さ。
