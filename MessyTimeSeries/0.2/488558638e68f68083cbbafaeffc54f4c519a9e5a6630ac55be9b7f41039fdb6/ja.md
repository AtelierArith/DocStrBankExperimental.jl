```
SizedKalmanStatus(...)
```

常に時刻 $T$ までのフィルタ履歴を保存する不変構造体を定義します。

# 引数

  * `online_status`: `OnlineKalmanStatus` 構造体
  * `history_length`: 履歴の長さ
  * `history_X_prior`: 事前の X の履歴
  * `history_X_post`: 事後の X の履歴
  * `history_P_prior`: 事前の P の履歴
  * `history_P_post`: 事後の P の履歴
  * `history_e`: 予測誤差の履歴
  * `history_inv_F`: 予測誤差共分散の逆数の履歴
  * `history_L`: ショートカット L の履歴
