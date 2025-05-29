`change_simulation_stop_criteria(m::ContinuousTimeModel, isabsorbing_func::Symbol)`

モデル `m` のシミュレーションを変更し、`isabsorbing_func::Symbol` という名前の関数に基づいて停止基準を追加します。`isabsorbing_func` は型シグネチャ `isabsorbing_func(p::Vector{Float64}, x::Vector{Int})` を持つ必要があり、ここで `p` はモデルのパラメータベクトル、`x` はモデルの状態（観測された状態ではない）です。
