```
Chunk(;
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

宣言的記憶チャンクを表すオブジェクト。

# キーワード

  * `N=1.0`: 使用回数
  * `L=1.0`: チャンクの寿命
  * `time_created=0.0`: チャンクが作成された時刻
  * `k=1`: 最近のセット内のチャンクの数（k=1で十分）
  * `act=0.0`: 総活性化
  * `act_blc=0.0`: 活性化の基準レベル定数成分
  * `act_bll=0.0`: 活性化の基準レベル学習成分
  * `act_pm=0.0`: 活性化の部分一致成分
  * `act_sa=0.0`: 活性化の拡散成分
  * `act_noise=0.0`: 活性化のノイズ成分
  * `slots`: チャンクのスロット-値ペア
  * `reps=0`: 同一チャンクの数。この値は、単純なケースでコードを高速化するために使用できます。
  * `recent=[0.0]`: k個の最近の取得のタイムスタンプ
  * `lags=Float64[]`: 最近の取得の遅延（L - recent）
  * `bl=0.0`: チャンクの活性化に追加される基準レベル定数

# 例

```@example
using ACTRModels

chunk = Chunk(; name = :Bonkers, animal = :rat)
```
