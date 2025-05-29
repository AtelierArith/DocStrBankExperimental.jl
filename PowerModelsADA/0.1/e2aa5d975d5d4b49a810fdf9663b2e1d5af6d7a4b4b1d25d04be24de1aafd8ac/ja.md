```
initialize_all_variable(data::Dict{String, <:Any}, model_type::DataType, dics_name::String="solution", initialization_method::String="flat")
```

すべての問題変数を含む辞書を返します。解を保存するために使用できます。

# 引数:

  * data::Dict{String, <:Any} : エリアデータ
  * model_type::DataType : 電力フローの定式化 (PowerModelタイプ)
  * dics_name::String="solution" : 出力を開始するために使用される既存の辞書の場所
  * initialization_method::String="flat" : "flat" または "worm" 初期化
