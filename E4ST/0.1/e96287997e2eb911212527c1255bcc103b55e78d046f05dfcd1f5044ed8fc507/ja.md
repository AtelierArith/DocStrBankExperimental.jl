```
modify_model!(mod::InterfaceLimit, config, data, model)
```

  * `interface_limit` テーブルの各行に対して、各ブランチ（前方および逆方向）を集めます。
  * 各インターフェースでの電力フローを MW 単位で表す式 `pflow_if[if_idx, yr_idx, hr_idx]` を作成します。これには以下が含まれます。

      * **f**から**t**への方向に流れているブランチのすべての `pflow_branch` 項の合計。
      * **t**から**f**への方向に流れているブランチのすべての `pflow_branch` 項の合計を差し引きます。
  * 各インターフェース制限に対して、制限が有限であり、インターフェースに適格な `pflow_branch` 変数がある各年および時間に対して、最小および最大制約 `cons_pflow_if_min[if_idx, yr_idx, hr_idx]` および `cons_pflow_if_max[if_idx, yr_idx, hr_idx]` を作成します。
  * 各インターフェース制限に対して、制限が有限であり、インターフェースに適格な `pflow_branch` 変数がある各年に対して、最小および最大制約 `cons_eflow_if_min[if_idx, yr_idx]` および `cons_eflow_if_max[if_idx, yr_idx]` を作成します。
  * インターフェースフローのコストを表す式 `interface_flow_cost_obj[if_idx, yr_idx, hr_idx]` を作成し、目的関数に追加します。
