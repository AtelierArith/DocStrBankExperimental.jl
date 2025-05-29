```julia
run_simulation(
    config::HallThruster.Config,
    sim::HallThruster.SimParams;
    postprocess,
    restart,
    kwargs...
) -> HallThruster.Solution{_A, P, C} where {_A, P<:NamedTuple, C<:HallThruster.Config}

```

提供された `Config` と `SimParams` オブジェクトを使用してホールスラスタシミュレーションを実行します。`Solution` オブジェクトを返します。

## 引数

  * `config::Config`: シミュレーションに関するジオメトリ、プラズマ特性、および数値情報を含みます。詳細については [Configuration](@ref) を参照してください。
  * `sim::SimParams`: グリッド生成およびタイムステッピング情報を含みます。詳細については [Simulations](@ref) を参照してください。
  * `postprocess::Union{Postprocess, Nothing}`: 出力が書き込まれるファイルを含み、どのような出力を記述するかを指定します。`nothing` の場合、ファイルには出力が書き込まれません。詳細については [Postprocessing](@ref) を参照してください。
  * `restart`::String: プラズマデータを含むJSONファイルへのオプションのパスです。空でない場合、ソリューションはそのファイルから再開されます。
