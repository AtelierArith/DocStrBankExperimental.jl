```
チャンク
```

宣言的メモリチャンクを表すオブジェクトです。

# フィールド

  * `N=1.0`: 使用回数
  * `L=1.0`: チャンクの寿命
  * `time_created=0.0`: チャンクが作成された時刻
  * `k=1`: 最近のセット内のチャンクの数（k=1で十分）
  * `act=0.0`: 総活性
  * `act_blc=0.0`: 活性の基準レベル定数成分
  * `act_bll=0.0`: 活性の基準レベル学習成分
  * `act_pm=0.0`: 活性の部分一致成分
  * `act_sa=0.0`: 活性の拡散活性成分
  * `act_noise=0.0`: 活性のノイズ成分
  * `slots`: チャンクのスロット-値ペア
  * `reps=0`: 同一のチャンクの数。この値は、単純なケースでコードの速度を上げるために使用できます。
  * `recent=[0.0]`: k回の最近の取得のタイムスタンプ
  * `lags=Float64[]`: 最近の取得の遅延（L - recent）
  * `bl=0.0`: チャンクの活性に追加される基準レベル定数
