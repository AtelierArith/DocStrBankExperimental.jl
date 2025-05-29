```
ksmoother(settings::KalmanSettings, status::KalmanStatus, t_stop::Int64=1)
```

カルマンスムーザー: `status` で評価された最後の時間期間から $t==0$ までの RTS スムーザー。

スムーザーは、Durbin と Koopman (2012) に提案されたアプローチに従って実装されています。

# 引数

  * `settings`: KalmanSettings 構造体
  * `status`: KalmanStatus 構造体
  * `t_stop`: 最後のスムージング期間を定義するために使用できるオプションの引数 (デフォルト: 1)
