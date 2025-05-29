```
fit_rate_equation(
    rate_equation::Function,
    data::DataFrame,
    metab_names::Tuple{Symbol, Vararg{Symbol}},
    param_names::Tuple{Symbol, Vararg{Symbol}};
    n_iter = 20
```

)

`rate_equation`を`data`にフィットさせ、損失と最適フィットパラメータを返します。

# 引数

  * `rate_equation::Function`: メタボライト濃度のNamedTuple（`metab_names`キーを持つ）とパラメータ（`param_names`キーを持つ）を受け取り、酵素の速度を返す関数。
  * `data::DataFrame`: 列`Rate`と各`metab_names`の列を持つデータを含むDataFrame。各行は1つの測定値です。また、データのソースを識別する文字列を含む`source`列も必要です。これは、出版物の各図の重みを計算するために使用されます。
  * `metab_names::Tuple{Symbol, Vararg{Symbol}}`: `rate_equation`のメタボライトに対応するメタボライト名のタプルと`data`の列名。
  * `param_names::Tuple{Symbol, Vararg{Symbol}}`: `rate_equation`のパラメータに対応するパラメータ名のタプル。
  * `n_iter::Int`: フィッティングプロセスを実行する反復回数。

# 戻り値

  * `loss::Float64`: 最適フィットの損失。
  * `params::NamedTuple`: `param_names`キーを持つ最適フィットパラメータ。

# 例

```julia
using DataFrames
data = DataFrame(
    Rate = [1.0, 2.0, 3.0],
    A = [1.0, 2.0, 3.0],
    source = ["Figure 1", "Figure 1", "Figure 2"]
)
rate_equation(metabs, params) = params.Vmax * metabs.S / (1 + metabs.S / params.K_S)
fit_rate_equation(rate_equation, data, (:A,), (:Vmax, :K_S))
```
