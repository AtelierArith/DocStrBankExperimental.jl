```
solve_dopf_aladin_coordinated(data::Dict{String, <:Any}, model_type::DataType, optimizer; tol::Float64=1e-4, 
max_iteration::Int64=1000, print_level = true, p::Real=1000, mu::Real=1000, p_upper::Real=1e6, mu_upper::Real=2e6, r_p::Real=1.5, mu_p::Real=2, a1::Real=1, a2::Real=1, #     a3::Real=1, q_gamma::Real=0, sigma::Dict{String,Real}=Dict())
```

ALADINアルゴリズムを使用して中央コーディネーターで分散OPF問題を解決します。

# 引数:

  * data::Dict{String, <:Any} : PowerModel形式のケースを含む辞書
  * model_type::DataType : 電力フローの定式化（PowerModelタイプ）
  * optimizer : JuMP初期化オブジェクト
  * mismatch_method::String="norm" : 不一致計算方法（norm, max）
  * tol::Float64=1e-4 : 不一致許容値
  * max_iteration::Int64=1000 : 最大反復回数
  * print_level::Int64=1 : 各反復後の不一致と結果の要約を印刷
  * p::Real=1000 : パラメータ
  * mu::Real=1000 : パラメータ
  * p_upper::Real=1e6 : パラメータ
  * mu_upper::Real=2e6 : パラメータ
  * r_p::Real=1.5 : パラメータ
  * r_mu::Real=2 : パラメータ
  * a1::Real=1 : パラメータ
  * a2::Real=1 : パラメータ
  * a3::Real=1 : パラメータ
  * q_gamma::Real=0 : パラメータ
  * sigma::Dict{String, <:Any}=Dict() : 変数名をキー、パラメータ値を値とする辞書
