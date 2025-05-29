```julia
struct SampleDefault{D<:BaytesCore.DataStructure, M<:BaytesCore.TemperingMethod, P<:BaytesCore.ProgressReport}
```

サンプリングルーチンのデフォルト引数。

# フィールド

  * `dataformat::BaytesCore.DataStructure`: 提案ステップの前にデータを分割するためのフォーマット。
  * `tempering::BaytesCore.TemperingMethod`: 各チェーンのターゲット分布のための温度値。デフォルトでは各チェーンに対して1*logtarget(θ | data)。
  * `chains::Int64`: サンプリングステップで実行されるチェーンの数。
  * `iterations::Int64`: MCMCの反復回数。SMCで上書きされる可能性があります。
  * `burnin::Int64`: バーンインサンプル。
  * `thinning::Int64`: 診断出力のために取得される連続サンプルの数。
  * `safeoutput::Bool`: トレースとアルゴリズムを作業ディレクトリに保存するかどうかのブール値。
  * `printoutput::Bool`: 要約統計量を計算するかどうかのブール値。
  * `printdefault::BaytesCore.PrintDefault`: 要約統計量を印刷するためのデフォルト引数。
  * `report::BaytesCore.ProgressReport`: サンプリング実行中の出力を印刷するためのデフォルト引数。
