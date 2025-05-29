# ニュートン

## コンストラクタ

```julia
Newton(; alphaguess = LineSearches.InitialStatic(),
linesearch = LineSearches.HagerZhang())
```

## 説明

`Newton` メソッドは、関数を最適化するためのニュートン法を実装しています。各探索方向が降下方向であることを保証するために、パッケージ `PositiveFactorizations.jl` からの特別な因子分解を使用します。ニュートン法の実践に関する議論については、Wright と Nocedal および Wright (ch. 6, 1999) を参照してください。

## 参考文献

  * Nocedal, J. and S. J. Wright (1999), Numerical optimization. Springer Science 35.67-68: 7.
