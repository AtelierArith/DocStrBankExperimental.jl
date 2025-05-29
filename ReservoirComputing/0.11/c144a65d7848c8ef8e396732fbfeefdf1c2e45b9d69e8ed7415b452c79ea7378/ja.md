```
create_states(reservoir_driver::AbstractReservoirDriver, train_data, washout,
    reservoir_matrix, input_matrix, bias_vector)
```

指定されたレザーバドライバーに従って、訓練されたエコー状態ネットワーク（ESN）の状態を作成して返します。

# 引数

  * `reservoir_driver`: ESNの状態が時間とともにどのように進化するかを決定するレザーバドライバー。
  * `train_data`: ESNを訓練するために使用される訓練データ。
  * `washout`: 初期条件を洗い流すために訓練中に破棄する初期時間ステップの数。
  * `reservoir_matrix`: ESNの動的で再帰的な部分を表すレザーバマトリックス。
  * `input_matrix`: 入力特徴とレザーバノード間の接続を定義する入力マトリックス。
  * `bias_vector`: レザーバの更新中に各時間ステップで追加されるバイアスベクトル。
