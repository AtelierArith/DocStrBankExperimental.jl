```
DynamicKalmanStatus(...)
```

任意のタイプのカルマンフィルタ出力を処理するための可変構造体を定義します。

カルマンフィルタの履歴は、フィルタ設定で `store_history` が true に設定されているときに保存されます。

# 引数

  * `t`: 現在の時点
  * `loglik`: 対数尤度
  * `X_prior`: 最新の事前 X
  * `X_post`: 最新の事後 X
  * `P_prior`: 最新の事前 P
  * `P_post`: 最新の事後 P
  * `e`: 予測誤差
  * `inv_F`: 予測誤差共分散の逆
  * `L`: フィルタとスムーザーの便利なショートカット
  * `buffer_J1`, `buffer_J2`, `buffer_m_m`, `buffer_m_n_obs`: 低レベルの行列操作に使用されるバッファ配列
  * `history_X_prior`: 事前 X の履歴
  * `history_X_post`: 事後 X の履歴
  * `history_P_prior`: 事前 P の履歴
  * `history_P_post`: 事後 P の履歴
  * `history_e`: 予測誤差の履歴
  * `history_inv_F`: 予測誤差共分散の逆の履歴
  * `history_L`: ショートカット L の履歴
