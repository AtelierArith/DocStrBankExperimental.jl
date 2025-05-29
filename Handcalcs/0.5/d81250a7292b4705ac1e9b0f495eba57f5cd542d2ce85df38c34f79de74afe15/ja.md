```
@handcalc expression
```

`expression`を表す`LaTeXString`を作成します。式は変数の後に等号と代数方程式が続きます。式の副作用、例えば代入は評価されます。RHSは、`post`というキーワード引数として関数を提供することでフォーマットまたはその他の変換が可能です。

# 例

```julia-repl
julia> a = 2
2
julia> b = 5
5
julia> @handcalc c = a + b
L"$c = a + b = 2 + 5 = 7$"

julia> c
7
```
