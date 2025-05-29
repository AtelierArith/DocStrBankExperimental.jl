```
out = simulate(obj::Phantom, seq::Sequence, sys::Scanner; sim_params, w)
```

`"return_type"`キーの値に応じて、生の信号または磁化の最終状態を返します。

これは`run_sim_time_iter`へのラッパー関数であり、入力を適切な型に変換し、シミュレーション前にシーケンスを離散化します。報告されたシミュレーション時間は`run_sim_time_iter`のみを考慮しており、前処理の時間はシミュレーション時間に比べて無視できるはずです（そうでない場合は、バグ報告をしてください）。

# 引数

  * `obj`: (`::Phantom`) Phantom構造体
  * `seq`: (`::Sequence`) Sequence構造体
  * `sys`: (`::Scanner`) Scanner構造体

# キーワード

  * `sim_params`: (`::Dict{String,Any}`, `=Dict{String,Any}()`) シミュレーションパラメータ辞書
  * `w`: (`::Blink.AtomShell.Window`, `=nothing`) Blink Window UIで進行状況バーを表示するウィンドウ。この変数が'nothing'以外の場合、進行状況バーが考慮されます。

# 戻り値

  * `out`: (`::Vector{Complex}`または`::SpinStateRepresentation`または`::RawAcquisitionData`) "return_type"が"mat"、"state"、または"raw"（デフォルト）であるかどうかに応じて

# 例

```julia-repl
julia> seq_file = joinpath(dirname(pathof(KomaMRI)), "../examples/5.koma_paper/comparison_accuracy/sequences/EPI/epi_100x100_TE100_FOV230.seq");

julia> sys, obj, seq = Scanner(), brain_phantom2D(), read_seq(seq_file)

julia> raw = simulate(obj, seq, sys)

julia> plot_signal(raw)
```
