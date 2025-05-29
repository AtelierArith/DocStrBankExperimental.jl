```julia
struct NUTS{S}
```

HoffmanとGelman（2014）の「No-U-Turn Sampler」の実装、及びBetancourt（2017）で説明されているその後の発展を含みます。

# フィールド

  * `max_depth`: 最大ツリー深度。
  * `min_Δ`: 発散を示す出発点に対する負のエネルギーの閾値。
  * `turn_statistic_configuration`: ターン統計の構成。現在サポートされているのは`Val(:generalized)`（デフォルト）のみです。
