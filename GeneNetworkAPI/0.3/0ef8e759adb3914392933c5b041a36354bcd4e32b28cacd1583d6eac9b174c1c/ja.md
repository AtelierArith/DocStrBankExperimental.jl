```
run_gemma(dataset::String,trait::String; use_loco::Bool=false, maf::Float64=0.01,
    gn_url::String=gn_url())
```

指定された `dataset` で指定された `trait` を使用して GEMMA を実行します。オプションの引数には以下が含まれます：

  * use_loco (デフォルト=false): LOCO（1つの染色体を除外する）を使用するかどうか
  * maf (デフォルト=0.01): スキャンされるマーカーの最小マイナーアレル頻度
