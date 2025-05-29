```julia
v, M = optimize([(f, set) ...], X, d)
```

変数 `X` において、制約または目的ペア `(f, set)` によって定義される、次数 `d` の緩和のモーメントプログラムを解きます。ここで、`f` は多項式で、`set` は文字列です。

  * "inf", "sup" は目的を定義します。
  * "=0" はゼロ制約を定義します。
  * ">=0", "<=0" は符号制約を定義します。

出力は次のとおりです。

  * v: 最適値
  * M: MOM.Model 型の最適化されたモーメントプログラム

## 例

```julia
using MomentPolynomialOpt

X  = @polyvar x1 x2
e1 = x1^2-2
e2 = (x2^2-3)*(x1*x2-2)
p1 = x1
p2 = 2-x2
v, M = optimize([(-x1, "inf"), (e1, "=0"), (e2, "=0"), (p1, ">=0"), (p2>=0)], X, 3)
```

最適値を取得するには、[`get_minimizers`](@ref)、[`get_measure`](@ref)、[`get_series`](@ref) を参照してください。
