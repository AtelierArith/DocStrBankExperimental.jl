```
modify_model!(pol::GenerationStandard, config, data, model)
```

式 :p*gs*bus を作成します。これは、生成基準が適用される負荷であり、まだ作成されていない場合に限ります。一般的な形式の制約を作成します: `sum(gs_egen * credit) <= gs_value * sum(gs_load)`
