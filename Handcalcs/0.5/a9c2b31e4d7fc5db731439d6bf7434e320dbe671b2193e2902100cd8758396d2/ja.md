```
@handfunc expression
```

`expressions`を表す`LaTeXString`を作成します。これらの式は、呼び出された関数内に存在するいくつかの式を表します。単一の式は、変数の後に等号と呼び出される関数が続く形です。この式も評価されます（関数内の式は評価されません）。RHSは、kwarg `post`として関数を供給することでフォーマットまたはその他の変換が可能です。

# 例

```julia-repl
julia> @handfunc Iy = calc_Ix(5, 15)
L"$\begin{aligned}
Ix &= \frac{b \cdot h^{3}}{12} = \frac{5 \cdot 15^{3}}{12} = 1406.25
\end{aligned}$"

julia> Iy
1406.25

```

Iyが評価される一方でIxは評価されないことに注意してください。
