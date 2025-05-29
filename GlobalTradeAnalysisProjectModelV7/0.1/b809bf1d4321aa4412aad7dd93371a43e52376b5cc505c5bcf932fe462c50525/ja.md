```
generate_calibration_inputs(model_container, start_data)
```

デフォルトキャリブレーションに必要な入力を生成します。キャリブレーションはGTAPデータベースの価値フローに焦点を当てています。

### 引数:

  * `model_container`: 現在のモデルを持つモデルコンテナ
  * `start_data`: 希望するキャリブレーションレベルを表すデータを含む辞書

### 戻り値

2つの要素を持つ名前付きタプル: `fixed_calibration` はクロージャを含み、`data_calibration` は希望するキャリブレーションデータを含みます。
