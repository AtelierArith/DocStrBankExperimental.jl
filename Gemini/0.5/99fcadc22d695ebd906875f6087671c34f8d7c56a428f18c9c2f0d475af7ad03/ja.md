新しい注文を作成します

https://docs.gemini.com/rest-api/#new-order

# 引数:

  * `sandbox::Bool`: サンドボックスリクエスト
  * `api_key::String`: Gemini APIキー
  * `api_secret::String`: Gemini APIシークレット
  * `side::String`: "buy" または "sell"
  * `symbol::String`: 新しい注文のシンボル
  * `amount::String`: 購入するための小数点付き金額
  * `price::String`: 単位あたりに支出するための小数点付き金額
  * `type::String`: 注文の種類。"exchange limit" はストップリミット注文以外のすべての注文タイプに対して。 "exchange stop limit" はストップリミット注文用。
  * `options::Vector{String}`:	Optional. 最大1つのサポートされている注文実行オプションを含むオプションの配列。
  * `stop_price::String`: オプション。ストップリミット注文をトリガーするための価格。ストップリミット注文にのみ利用可能。
