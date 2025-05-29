```
solve_dopf_app(data::Dict{String, <:Any}, model_type::DataType, optimizer; 
mismatch_method::String="norm",tol::Float64=1e-4, max_iteration::Int64=1000, 
print_level::Int64=1, alpha::Real=1000, beta::Real, gamma::Real)
```

APPアルゴリズムを使用して分散OPF問題を解決します。

# 引数:

  * data::Dict{String, <:Any} : PowerModel形式のケースを含む辞書
  * model_type::DataType : 電力フローの定式化（PowerModel型）
  * optimizer : JuMP初期化オブジェクト
  * mismatch_method::String="norm" : 不一致計算方法（norm, max）
  * tol::Float64=1e-4 : 不一致許容値
  * max_iteration::Int64=1000 : 最大反復回数
  * print_level::Int64=1 : 各反復後の不一致と結果の概要を印刷
  * alpha::Real=1000 : アルゴリズムパラメータ
  * beta::Real=2alpha : アルゴリズムパラメータ
  * gamma::Real=alpha : アルゴリズムパラメータ
