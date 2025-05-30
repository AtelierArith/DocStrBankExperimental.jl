```julia
struct TraceSummary{A<:BaytesCore.TemperingMethod, B<:Union{BaytesCore.DataTune, Vector{<:BaytesCore.DataTune}}, D<:BaytesCore.SampleDefault, S<:Baytes.SampleInfo}
```

サンプリング後の分析に役立つ情報を含みます。また、指定されたサンプラーでサンプリングを続行することも可能です。

# フィールド

  * `tempertune::BaytesCore.TemperingMethod`: 温度テンプリングのための調整コンテナ
  * `datatune::Union{BaytesCore.DataTune, Vector{<:BaytesCore.DataTune}}`: データテンプリングのための調整コンテナ
  * `default::BaytesCore.SampleDefault`: サンプル関数に使用されるデフォルト設定
  * `info::Baytes.SampleInfo`: 後処理に使用されるトレースに関する情報。
  * `progress::ProgressMeter.Progress`: サンプリング中の進捗ログ。
