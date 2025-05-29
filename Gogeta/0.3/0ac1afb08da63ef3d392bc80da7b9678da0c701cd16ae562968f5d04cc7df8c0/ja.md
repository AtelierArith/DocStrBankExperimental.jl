```
function check_ICNN(optimizer, filepath, output_value, input_values...; show_output=true, negated=false)
```

ICNNがより大きな最適化問題の定式化に含まれている出力が正しいことを確認します。ICNN LP定式化は不適合を検出できないため、検証が必要です。

ICNNの出力が正しい場合はtrueを、そうでない場合はfalseを返します。

# 引数

  * `optimizer`: JuMPオプティマイザオブジェクト
  * `filepath`: モデルパラメータを含むJSONファイルへの相対パス
  * `output_value`: より大きな最適化問題の最適解におけるICNNの出力
  * `input_values`: より大きな最適化問題の最適解におけるICNNの入力の値

# キーワード引数

  * `show_output`: コンソールに追加情報を印刷する
  * `negated`: ICNNがデータを否定してトレーニングされている場合は'true'に設定する
