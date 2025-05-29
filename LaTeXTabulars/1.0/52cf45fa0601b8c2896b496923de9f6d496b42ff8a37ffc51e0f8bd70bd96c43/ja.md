```julia
latex_tabular(io, t, lines; formatter)

```

指定された環境を使用して、`lines`を`io`にLaTeX形式で印刷します。

`lines`内の各`line`は次のようになります。

  * ルールのようなオブジェクト、例えば[`Rule`](@ref)や[`CMidRule`](@ref)、
  * セルの反復可能なもの（例：`AbstractVector`）、
  * 複数の行として扱われる`Tuple`（「スプラット」）、これは関連するルールや複数の`CMidRule`を持つ行を生成する関数に便利です、
  * 各行が1行として扱われる行列。

セルを含む構造は[`latex_cell`](@ref)によって印刷され、`formatter`を使用して文字列と`LaTeX`セルはそのままにします。

テーブルの部分のフォーマットは、適切なフォーマッタを使用して引数に直接行うことをお勧めします。例についてはマニュアルを参照してください。

サポートされているセルの種類については[`latex_cell`](@ref)を参照してください（特に[`MultiColumn`](@ref)ですが、完全なフォーマット制御のためには、セルに`String`または`LaTeXString`を使用してください）。
