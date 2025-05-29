```
ft_latex_sn(m_digits::Int, [columns::AbstractVector{Int}]) -> Function
```

`columns`の要素の数をLaTeXを使用して科学的表記にフォーマットします。数値は最初に`Printf`関数を使用して`g`修飾子で印刷され、その後LaTeX形式に変換されます。仮数部の桁数は引数`m_digits`で選択できます。

`m_digits`が`Vector`の場合、`columns`も同じ数の要素を持つ`Vector`でなければなりません。`m_digits`が`Integer`で、`columns`が指定されていない（または空である）場合、フォーマットはテーブル全体に適用されます。そうでなければ、`m_digits`が`String`で、`columns`が`Vector`の場合、フォーマットは`columns`内の列のみに適用されます。

!!! info
    このフォーマッタは、`Number`型のセルにのみ適用されます。

