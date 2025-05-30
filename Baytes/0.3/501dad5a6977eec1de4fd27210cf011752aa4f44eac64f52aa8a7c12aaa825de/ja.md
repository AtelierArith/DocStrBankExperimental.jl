```julia
struct SampleInfo{A<:Baytes.PrintedParameter, U<:BaytesCore.UpdateBool, B<:BaytesCore.UpdateBool}
```

サンプラーを構築するためのいくつかの有用な情報を含みます。

# フィールド

  * `printedparam::Baytes.PrintedParameter`: 印刷のためのパラメータ設定。
  * `iterations::Int64`: サンプリング反復の総数。
  * `burnin::Int64`: バーンイン反復。
  * `thinning::Int64`: 診断出力のために取得される連続サンプルの数。
  * `Nalgorithms::Int64`: サンプリング中に使用されるアルゴリズムの数。
  * `Nchains::Int64`: サンプリング中に使用されるチェーンの数。
  * `captured::BaytesCore.UpdateBool`: 提案実行後にサンプラーを更新する必要があるかどうかのブール値。これは、例えばPMCMCや適応的温度調整の場合です。
  * `tempered::BaytesCore.UpdateBool`: 目標関数のために温度が適応されているかどうかのブール値。
