```
solve_dopf(data::Dict{String, <:Any}, model_type::DataType, optimizer, dopf_method::Module; print_level::Int64=1, multiprocessors::Bool=false, mismatch_method::String="norm", tol::Float64=1e-4, max_iteration::Int64=1000, save_data::Vector{String}=[], kwargs...)
```

完全分散アルゴリズムを使用してOPF問題を解決します。

# 引数:

  * data::Dict{String, <:Any} : PowerModel形式のケースを含む辞書
  * model_type::DataType : 電力フローの定式化 (PowerModel型)
  * optimizer : JuMP初期化オブジェクト
  * dopf_method::Module : 分散アルゴリズムメソッドを含むモジュールは以下の通りです:

      * initialize_method::Function : アルゴリズムのパラメータと共有変数を初期化
      * update_method::Function : 各イテレーション後にアルゴリズムを更新
      * build_method::Function : 問題の定式化
  * print_level::Int64=1 : 0 - 印刷なし, 1 - 各イテレーション後のミスマッチと結果の概要を印刷, 2 - オプティマイザの出力を印刷
  * multiprocessors::Bool=false : 利用可能なワーカーを使用してマルチプロセッサを有効にします。マルチプロセッサ機能は、すべてのプロセッサで@everywhereを使用してPowerModelsADAおよびオプティマイザパッケージをロードする必要があります。
  * mismatch_method::String="norm" : ミスマッチ計算方法 (norm, max)
  * tol::Float64=1e-4 : ミスマッチ許容値
  * max_iteration::Int64=1000 : 最大イテレーション数
  * save*data::Vector{String}=[] : 各イテレーションで"previous*solution"に保存される辞書のキーを含むベクター。例えば、save*data=["solution", "shared*variable", "mismatch"]
  * kwargs = アルゴリズム特有の初期化パラメータを含む
