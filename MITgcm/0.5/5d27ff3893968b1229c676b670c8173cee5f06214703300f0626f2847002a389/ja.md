```
setup(config::MITgcm_config)
```

`run/` フォルダーを作成し、必要に応じてすべてをそこにリンクして、ほとんどの標準的な MITgcm 構成に対して通常行われるようにモデルを実行できるようにします（`prepare_run` と `mitgcmuv` を含む）。`ClimateModels.git_log_init(config)` を呼び出して git トラッカーを設定し、後で `launch(config)` を介して実行されるように `put!(config.channel,MITgcm_launch)` を実行します。

（`MITgcm` 用に特化された気候モデルインターフェースの一部）
