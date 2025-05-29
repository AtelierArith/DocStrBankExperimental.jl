```
qec_run(
    code, error_model, decoder, p::Real, random_seed=nothing;
    max_runs::Union{Integer,Nothing}=nothing,
    max_failures::Union{Integer,Nothing}=nothing
) -> Dict
```

安定器コードのエラー復旧（理想的）シミュレーションを複数回実行し、集約された実行データを返します。単一の実行の詳細については、[`qec_run_once`](@ref)を参照してください。

パラメータ`code`、`error_model`、および`decoder`は、それぞれ[`StabilizerCode`](@ref)、[`ErrorModel`](@ref)、および[`Decoder`](@ref)の具体的なサブタイプまたはダックタイピングされた実装である必要があります。

シミュレーションは、`max_runs`および`max_failures`によって決定される回数だけ実行されます。`max_runs`および/または`max_failures`が指定されている場合、最初に発生した方（`max_runs`回の実行または`max_failures`回の失敗）の後に停止します。どちらも指定されていない場合は、1回の実行の後に停止します。

返される集約データは次の形式を持ちます：

```
Dict(
    :code => "5-qubit"              # label(code)
    :n_k_d => (5, 1, 3)             # nkd(code)
    :time_steps => 1                # 理想的なシミュレーションでは常に1
    :error_model => "Depolarizing"  # label(error_model)
    :decoder => "Naive"             # label(decoder)
    :error_probability => 0.1       # p
    :measurement_error_probability => 0.0   # 理想的なシミュレーションでは常に0.0
    :n_run => 100                   # 実行回数
    :n_success => 92                # 成功した復旧の回数
    :n_fail => 8                    # 失敗した復旧の回数
    :n_logical_commutations => [5, 6]   # 論理的交換の回数
    :custom_totals => nothing       # custom_valuesの合計
    :error_weight_total => 55       # n_run回の実行におけるerror_weightの合計
    :error_weight_pvar => 0.4075    # n_run回の実行におけるerror_weightのp分散
    :logical_failure_rate => 0.08   # n_fail / n_run
    :physical_error_rate => 0.11    # error_weight_total / n_k_d[1] / time_steps / n_run
    :wall_time => 0.00253906        # 実行の壁時間（小数秒）
)
```

# 例

```jldoctest; filter = r":wall_time +=> \d*\.?\d*"
julia> using Qecsim.BasicModels, Qecsim.GenericModels

julia> seed = 7;

julia> data = qec_run(FiveQubitCode(), DepolarizingErrorModel(), NaiveDecoder(), 0.1, seed;
           max_runs=100);
┌ Info: qec_run: 開始
│   code = Qecsim.BasicModels.BasicCode(["XZZXI", "IXZZX", "XIXZZ", "ZXIXZ"], ["XXXXX"], ["ZZZZZ"], (5, 1, 3), "5-qubit")
│   error_model = Qecsim.GenericModels.DepolarizingErrorModel()
│   decoder = Qecsim.GenericModels.NaiveDecoder(10)
│   p = 0.1
│   random_seed = 7
│   max_runs = 100
└   max_failures = nothing
[ Info: qec_run: rng=MersenneTwister(7)
[ Info: qec_run: 完了: data=Dict{Symbol, Any}(:error_weight_pvar => 0.4075000000000001, :time_steps => 1, :n_logical_commutations => [5, 6], :error_weight_total => 55, :wall_time => 0.002539058, :n_k_d => (5, 1, 3), :error_model => "Depolarizing", :physical_error_rate => 0.11, :measurement_error_probability => 0.0, :error_probability => 0.1, :n_success => 92, :logical_failure_rate => 0.08, :custom_totals => nothing, :code => "5-qubit", :decoder => "Naive", :n_fail => 8, :n_run => 100)

julia> data
Dict{Symbol, Any} with 17 entries:
  :error_weight_pvar             => 0.4075
  :time_steps                    => 1
  :n_logical_commutations        => [5, 6]
  :error_weight_total            => 55
  :wall_time                     => 0.00253906
  :n_k_d                         => (5, 1, 3)
  :error_model                   => "Depolarizing"
  :physical_error_rate           => 0.11
  :measurement_error_probability => 0.0
  :error_probability             => 0.1
  :n_success                     => 92
  :logical_failure_rate          => 0.08
  :custom_totals                 => nothing
  :code                          => "5-qubit"
  :decoder                       => "Naive"
  :n_fail                        => 8
  :n_run                         => 100
```
