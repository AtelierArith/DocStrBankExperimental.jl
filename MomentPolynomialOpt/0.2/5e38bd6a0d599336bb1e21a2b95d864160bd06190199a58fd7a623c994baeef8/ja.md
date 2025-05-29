```julia
v, M = optimize(sense, f, [e1, e2, ...], [p1, p2, ...], X, d)
```

変数 `X` におけるモーメントの次数 `d` の緩和を使用して、制約 $e_i$ =0 および $p_i \geq 0$ の下で `f` の最適値を計算します。

  * $$
    f, e_i, p_i
    $$

    は変数 X の多項式である必要があります。
  * 'sense` は [:Inf, :inf, :Min,:min] または :Sup, :sup, :Max, :max のシンボルです。
  * `X` は変数のタプルです。
  * `d` は緩和の次数です。
  * `optimizer` はモーメント緩和を解決するために使用されるオプティマイザです。デフォルトは `MMT[:optimizer]` です。

問題が実行可能で最小化子が存在する場合、次のように出力されます。

  * v: 最適値
  * M: JuMP.Model 型のモーメントモデル

## 例

```julia
using MomentPolynomialOpt

X  = @polyvar x1 x2
e1 = x1^2-2
e2 = (x2^2-3)*(x1*x2-2)
p1 = x1
p2 = 2-x2
v, M = optimize(:inf, -x1, [e1, e2], [p1, p2], X, 3)
```

オプティマイザを回収するには、[`get_minimizers`](@ref)、[`get_measure`](@ref)、[`get_series`](@ref) を参照してください。
