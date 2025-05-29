```
solve_dopf_coordinated(data::Dict{String, <:Any}, model_type::DataType, optimizer, dopf_method::Module; print_level::Int64=1, multiprocessors::Bool=false, mismatch_method::String="norm", tol::Float64=1e-4, max_iteration::Int64=1000, save_data::Vector{String}=[], kwargs...)
```

中央コーディネーターを使用した分散アルゴリズムでOPF問題を解決します。

# 引数:

  * data::Dict{String, <:Any} : PowerModel形式のケースを含む辞書
  * model_type::DataType : 電力フローの定式化 (PowerModel型)
  * optimizer : JuMP初期化オブジェクト
  * dopf_method::Module : 以下の分散アルゴリズムメソッドを含むモジュール:

      * initialize*method*local::Function : ローカルアルゴリズムのパラメータと共有変数を初期化
      * initialize*method*coordinator::Function : コーディネーターアルゴリズムのパラメータと共有変数を初期化
      * update*method*local::Function : 各イテレーション後にローカルデータを更新
      * update*method*coordinator::Function : 各イテレーション後にコーディネーターデータを更新
      * build*method*local::Function : ローカル問題の定式化
      * build*method*coordinator::Function : コーディネーター問題の定式化
  * print_level::Int64=1 : 0 - 印刷なし, 1 - 各イテレーション後のミスマッチと結果の要約を印刷, 2 - オプティマイザーの出力を印刷
  * multiprocessors::Bool=false : 利用可能なワーカーを使用してマルチプロセッサを有効にします。マルチプロセッサ機能は、すべてのプロセッサで@everywhereを使用してPowerModelsADAおよびオプティマイザーパッケージをロードする必要があります。
  * mismatch_method::String="norm" : ミスマッチ計算方法 (norm, max)
  * tol::Float64=1e-4 : ミスマッチ許容値
  * max_iteration::Int64=1000 : 最大イテレーション数
  * save*data::Vector{String}=[] : 各イテレーションで"previous*solution"に保存される辞書のキーを含むベクター。例えば、save*data=["solution", "shared*variable", "mismatch"]
  * kwargs = アルゴリズム特有の初期化パラメータを含む
