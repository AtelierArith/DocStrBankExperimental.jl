```
struct AnnualCapacityFactorLimit <: Modification

AnnualCapacityFactorLimit(;name, file)
```

発電機の年間容量係数制限を設定します。年間容量係数は、1年間に生成された総エネルギーを年間のエネルギー容量（電力容量と年間の時間数の積）で割ったものとして定義されます。

  * `modify_raw_data!` - `file`からテーブルを読み込み、`data[<name>]`に格納します。`summarize*table(::Val{:annual*cf_lim})`を参照してください。
  * `modify_model!` - 次の制約と式を設定します。

      * 各発電機の年間エネルギー生成のために`model[:egen_gen_annual]` (ngen x nhr)の式を設定します。
      * `file`で指定されたテーブルの各行によってカバーされる各発電機のために、`annual_cf_min`列が与えられている場合、制約`model[:cons_<name>_min]`を作成します。
      * `file`で指定されたテーブルの各行によってカバーされる各発電機のために、`annual_cf_max`列が与えられている場合、制約`model[:cons_<name>_max]`を作成します。

```
