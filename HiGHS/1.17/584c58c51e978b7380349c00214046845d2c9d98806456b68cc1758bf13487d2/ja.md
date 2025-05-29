```
Highs_getRanging(highs, col_cost_up_value, col_cost_up_objective, col_cost_up_in_var, col_cost_up_ou_var, col_cost_dn_value, col_cost_dn_objective, col_cost_dn_in_var, col_cost_dn_ou_var, col_bound_up_value, col_bound_up_objective, col_bound_up_in_var, col_bound_up_ou_var, col_bound_dn_value, col_bound_dn_objective, col_bound_dn_in_var, col_bound_dn_ou_var, row_bound_up_value, row_bound_up_objective, row_bound_up_in_var, row_bound_up_ou_var, row_bound_dn_value, row_bound_dn_objective, row_bound_dn_in_var, row_bound_dn_ou_var)
```

すべてのコストと制約の範囲情報を計算します。非基本変数に対して、範囲情報はアクティブな制約に関連しています。基本変数に対して、範囲情報は...

必要ない値はNULLを渡してください。

### パラメータ

  * `highs`: Highsインスタンスへのポインタ。
  * `col_cost_up_value`: コスト値の上限範囲
  * `col_cost_up_objective`: 上限コスト範囲での目的
  * `col_cost_up_in_var`: 上限コスト範囲で基準に入る変数
  * `col_cost_up_ou_var`: 上限コスト範囲で基準から出る変数
  * `col_cost_dn_value`: コスト値の下限範囲
  * `col_cost_dn_objective`: 下限コスト範囲での目的
  * `col_cost_dn_in_var`: 下限コスト範囲で基準に入る変数
  * `col_cost_dn_ou_var`: 下限コスト範囲で基準から出る変数
  * `col_bound_up_value`: 列制約値の上限範囲
  * `col_bound_up_objective`: 上限列制約範囲での目的
  * `col_bound_up_in_var`: 上限列制約範囲で基準に入る変数
  * `col_bound_up_ou_var`: 上限列制約範囲で基準から出る変数
  * `col_bound_dn_value`: 列制約値の下限範囲
  * `col_bound_dn_objective`: 下限列制約範囲での目的
  * `col_bound_dn_in_var`: 下限列制約範囲で基準に入る変数
  * `col_bound_dn_ou_var`: 下限列制約範囲で基準から出る変数
  * `row_bound_up_value`: 行制約値の上限範囲
  * `row_bound_up_objective`: 上限行制約範囲での目的
  * `row_bound_up_in_var`: 上限行制約範囲で基準に入る変数
  * `row_bound_up_ou_var`: 上限行制約範囲で基準から出る変数
  * `row_bound_dn_value`: 行制約値の下限範囲
  * `row_bound_dn_objective`: 下限行制約範囲での目的
  * `row_bound_dn_in_var`: 下限行制約範囲で基準に入る変数
  * `row_bound_dn_ou_var`: 下限行制約範囲で基準から出る変数

### 戻り値

呼び出しが成功したかどうかを示す`kHighsStatus`定数。
