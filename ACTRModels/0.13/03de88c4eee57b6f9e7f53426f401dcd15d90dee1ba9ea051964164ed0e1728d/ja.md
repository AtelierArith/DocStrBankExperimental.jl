```
Chunk(dynamic::Bool; 
    N = 1,
    L = 1.0,
    time_created = 0.0,
    k = 1, 
    act = 0.0, 
    recent = [0.0],
    reps = 0, 
    lags = Float64[], 
    bl = zero(typeof(act)),
    slots...)
```

動的スロット値ペアを持つ宣言的メモリチャンク。

# フィールド

  * `dynamic::Bool`: スロット値ペアはtrueの場合に可変
  * `N=1.0`: 使用回数
  * `L=1.0`: チャンクの寿命
  * `time_created=0.0`: チャンクが作成された時刻
  * `k=1`: 最近のセット内のチャンク数（k=1で十分）
  * `act_mean`: `act` - `act_noise`として計算された平均活性化
  * `act=0.0`: `act_mean` + `act_noise`として計算された総活性化
  * `act_blc=0.0`: 活性化の基準レベル定数成分
  * `act_bll=0.0`: 活性化の基準レベル学習成分
  * `act_pm=0.0`: 活性化の部分一致成分
  * `act_sa=0.0`: 活性化の拡散成分
  * `act_noise=0.0`: 活性化のノイズ成分
  * `slots`: チャンクスロット値ペア
  * `reps=0`: 同一チャンクの数。この値は単純なケースでコードを高速化するために使用できます。
  * `recent=[0.0]`: k回の最近の取得のタイムスタンプ
  * `lags=Float64[]`: 最近の取得の遅延（L - recent）
  * `bl=0.0`: チャンクの活性化に加えられる基準レベル定数
