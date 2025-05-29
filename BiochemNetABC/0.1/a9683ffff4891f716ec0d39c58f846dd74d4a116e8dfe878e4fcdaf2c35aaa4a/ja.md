`simulate(pm::ParametricModel, p_prior::AbstractVector{Float64})`

パラメトリックモデル `pm` に含まれるモデルを `p_prior` パラメータでシミュレートします。これは、`get_proba_model(pm).p` に含まれるパラメータを取り、1D パラメータ pm.params を `p_prior` で置き換えることによってモデルをシミュレートします。
