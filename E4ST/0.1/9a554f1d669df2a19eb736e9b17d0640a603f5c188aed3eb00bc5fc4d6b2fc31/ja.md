```
struct CCUS <: Modification

CCUS(;file, groupby, co2_scalar=1e5, co2_step_quantity_limit=1e9)
```

これは、発電所によって捕集された炭素の市場を設定する[`Modification`](@ref)です。

  * `file` - 二酸化炭素の売買に関する市場/価格を含むテーブルへのファイル。以下の`ccus_paths`テーブルを参照するか、[`summarize_table(::Val{:ccus_paths})`](@ref)を参照してください。
  * `groupby` - 市場がどのようにグループ化されるかを示す`String`。すなわち、「州」。
  * `co2_scalar` - CO₂変数をどれだけスケールするかを示す`Float64`。これは、いくつかのCO₂ステップが非常に大きくなり、モデルのRHSおよび境界範囲を膨らませる可能性があるため、数値的不安定性を助けます。良い目安は、これが`co2_step_quantity_limit`の`1e4`倍よりも小さくないべきということです。
  * `co2_step_quantity_limit` - 任意のステップで保存できるCO₂の最大量を示す`Float64`。

`data`に以下のテーブルを作成します：

  * `ccus_paths` - CO₂を売るためのすべての経路を含みます。

      * `producing_region` - 生産地域
      * `storing_region` - 経路の保存地域
      * `ccus_type` - ccusのタイプ（`eor`または`saline`）
      * `step_id` - ステップの番号（帳簿管理以外にはあまり重要ではありません）
      * `step_quantity` - このステップで保存できるCO₂の量
      * `price_trans` - `producing_region`から`storing_region`に1ショートトンのCO₂を輸送するコスト
      * `price_store` - ステップで1ショートトンのCO₂を保存するコスト
  * `ccus_storers` - すべてのストレージを含みます

      * `storing_region` - 保存地域
      * `step_id` - 地域のステップ番号
      * `ccus_type` - ステップが`eor`または`saline`であるかどうか。
      * `step_quantity` - ステップで保存できるショートトンの数
      * `price_store` - 1ショートトンのCO₂を保存するための価格。
      * `path_idxs` - このステップで炭素を保存するための輸送経路を表すインデックスのリスト。`ccus_paths`テーブルへのインデックス。
  * `ccus_producers` - `ccus_type`と`producing_region`でグループ化されたすべての生産者を含みます。これには以下の列が含まれます：

      * `producing_region` - CO₂が送信される地域
      * `ccus_type` - CO₂が送信されるステップのタイプ（`eor`または`saline`）
      * `path_idxs` - このステップから炭素を送信するための輸送経路を表すインデックスのリスト。`ccus_paths`テーブルへのインデックス。
      * `gen_idxs` - この地域でCO₂を生成する発電機のインデックスのリスト。

以下の変数/式を作成します

  * `co2_trans[1:nrow(ccus_paths), 1:nyear]` - この生産者-生産者経路に沿って輸送されるCO₂の量（変数）
  * `co2_stor[1:nrow(ccus_storers), 1:nyear]` - 各ストレージによって保存されるCO₂の量（`co2_trans`の式）
  * `co2_prod[1:nrow(ccus_producers), 1:nyear]` - 各送信地域によって生成されるCO₂の量（電力生成の式）
  * `co2_sent[1:nrow(ccus_producers), 1:nyear]` - 各送信地域から送信されるCO₂の量（`co2_trans`の式）。これには同じ地域内で送信されたCO₂が含まれます。
  * `cost_ccus_obj[1:nyear]` - 目的関数に追加されるccusの総コスト。

以下の制約を作成します

  * `cons_co2_stor[1:nrow(ccus_storers), 1:nyear]` - 各注入サイトで保存されるCO₂は`step_quantity`を超えてはならない
  * `cons_co2_bal[1:nrow(ccus_producers), 1:nyear]` - 各地域のCO₂バランス方程式、すなわち`co2_prod == co2_sent`。

## 結果のアクセス

結果は2つの場所に保存されます；`ccus_paths`テーブルと`gen`テーブル。

例の結果クエリ

  * `compute_result(data, :gen, :stored_co2_total, :ccus_type=>"eor", "y2030")`
  * `compute_result(data, :gen, :cost_capt_co2, :ccus_type=>"eor", yr_idx)`
  * `compute_result(data, :gen, :cost_capt_co2_store, :gentype=>"coalccs", yr_idx)`
  * `compute_result(data, :gen, :cost_capt_co2_trans, :, yr_idx)`
  * `compute_result(data, :ccus_paths, :storer_cost_total, :storing_region=>"narnia")`
  * `compute_result(data, :ccus_paths, :storer_revenue_total, :producing_region=>"narnia")`
  * `compute_result(data, :ccus_paths, :storer_profit_total, :ccus_type=>"eor")`

参照：

  * [`modify_raw_data!(::CCUS, config, data)`](@ref)
  * [`modify_setup_data!(::CCUS, config, data)`](@ref)
  * [`modify_model!(::CCUS, config, data, model)`](@ref)
  * [`modify_results!(::CCUS, config, data)`](@ref)

```
