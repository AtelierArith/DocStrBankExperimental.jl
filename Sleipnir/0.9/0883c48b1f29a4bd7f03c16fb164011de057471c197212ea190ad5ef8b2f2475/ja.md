```
plot_glacier_vid(
    plot_type::String,
    H::Vector{Matrix{Float64}},
    glacier::Glacier2D,
    simuparams::SimulationParameters,
    pathVideo::String;
    framerate::Int=24,
    baseTitle::String=""
)
```

氷河データのさまざまなタイプのビデオを生成します。現在のところ、氷河の氷厚の進化のみがサポートされています。将来的には、より多くの視覚化タイプが追加される予定です。

# 引数

  * `plot_type`: 生成するプロットのタイプ。オプションは次のとおりです：

      * "thickness": 氷河の厚さのヒートマップ。
  * `H`: 時間にわたる氷厚を含む行列のベクトル。これは、Resultsが氷流モデルに依存しなくなったときにResultsインスタンスに置き換えられるべきです。
  * `glacier`: 氷河のインスタンス。
  * `simuparams`: シミュレーションパラメータ。
  * `pathVideo`: 生成するmp4ファイルのパス。

# オプションのキーワード引数

  * `framerate`: ビデオ生成に使用するフレームレート。
  * `baseTitle`: フレームのタイトルに使用するプレフィックス。各フレームでは、" (t=XXXX)"の形式で年の値と連結されます。
