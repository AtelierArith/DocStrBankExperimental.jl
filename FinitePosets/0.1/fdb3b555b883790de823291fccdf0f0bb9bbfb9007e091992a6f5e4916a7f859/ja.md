`nlinear_extensions(P;lim=10^7)`  は、 `P` が `Poset` または `CPoset` の場合に、 `P` の線形拡張の数を返します。この数が `>lim` の場合はエラーを返します（デフォルトの 10^7 は数秒で達成されます）。

```julia-repl
julia> nlinear_extensions(CPoset(:antichain,10))
3628800
```
