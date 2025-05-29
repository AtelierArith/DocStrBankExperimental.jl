```
@handcalcs(expressions, kwargs)
```

`expressions`を表す`LaTeXString`を作成します。式は複数の式を表します。単一の式は変数の後に等号と代数方程式が続きます。式の副作用、例えば代入は評価されます。RHSは、kwarg `post`として関数を供給することでフォーマットまたはその他の変換が可能です。また、方程式の末尾にコメントを追加することもできます。以下の例を参照してください。

## Kwargs

  * cols: 出力の列数を設定します
  * spa: 行間隔を設定します
  * len: `:long`に設定すると、方程式を複数行に分割します
  * color: 出力の色を変更します（`:blue`, `:red`など）
  * h_env: "aligned"（デフォルト）、"align"およびその他のLaTeXオプションの中から選択します
  * not_funcs: "unroll"したくない関数の名前を指定します

# 例

```julia-repl
julia> a = 2
2

julia> b = 5
5

julia> e = 7
7

julia> @handcalcs begin 
    c = a + b; "eq 1";
    d = a - c
    e
end
L"$\begin{aligned}
c &= a + b = 2 + 5 = 7\;\text{  }(\text{eq 1})
\\[10pt]
d &= a - c = 2 - 7 = -5
\\[10pt]
e &= 7
\end{aligned}$"

julia> c
7

julia> d
-5

```
