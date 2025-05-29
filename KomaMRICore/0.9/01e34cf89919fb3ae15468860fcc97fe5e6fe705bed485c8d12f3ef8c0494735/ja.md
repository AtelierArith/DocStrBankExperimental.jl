```
raw = signal_to_raw_data(signal, seq; phantom_name, sys, sim_params)
```

生の信号を再構築に使用されるRawAcquisitionData構造体（ISMRMRD形式にほぼ相当）に変換します。

# 引数

  * `signal`: (`::Matrix{Complex}`) 生信号行列
  * `seq`: (`::Sequence`) シーケンス構造体

# キーワード

  * `phantom_name`: (`::String`, `="Phantom"`) ファントム名
  * `sys`: (`::Scanner`, `=Scanner()`) スキャナー構造体
  * `sim_params`: (`::Dict{String, Any}`, `=Dict{String,Any}()`) シミュレーションパラメータ辞書

# 戻り値

  * `raw`: (`::RawAcquisitionData`) RawAcquisitionData構造体

# 例

```julia-repl
julia> seq_file = joinpath(dirname(pathof(KomaMRI)), "../examples/1.sequences/epi_se.seq")

julia> sys, obj, seq = Scanner(), brain_phantom2D(), read_seq(seq_file)

julia> sim_params = KomaMRICore.default_sim_params(); sim_params["return_type"] = "mat"

julia> signal = simulate(obj, seq, sys; sim_params)

julia> raw = signal_to_raw_data(signal, seq)

julia> plot_signal(raw)
```
