```julia
default_warmup_stages(
;
    stepsize_search,
    M,
    stepsize_adaptation,
    init_steps,
    middle_steps,
    doubling_stages,
    terminating_steps
)

```

ウォームアップステージのシーケンス：

1. `stepsize_search`を使用して初期のステップサイズを選択します（デフォルト：ヒューリスティックに基づく）。
2. `init_steps`ステップでステップサイズを調整します。
3. ステップサイズと共分散を調整します：最初に`middle_steps`ステップで、次に`doubling_stages`回、2倍のステップで繰り返します。
4. `terminating_steps`ステップでステップサイズを調整します。

`M`（`Diagonal`、デフォルトまたは`Symmetric`）は、サンプルから適応されたメトリックのタイプを決定します。

これはほとんどのアプリケーションの推奨チューナーです。

`stepsize_adaptation`に`nothing`を使用して、対応するステップをスキップします。
