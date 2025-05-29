```
Metropolis(chains; pool=missing, sweepstep=1, seed=1, R=Xoshiro, parallel=false, extras...)
```

新しいMetropolisインスタンスを作成します。

# 引数

  * `chains`: アルゴリズムを実行するシステムのベクター
  * `pool`: スイープを実行するための移動のプール
  * `sweepstep`: スイープごとのモンテカルロステップの数
  * `seed`: ランダム数シード
  * `R`: ランダム数生成器のタイプ
  * `parallel`: 異なるスレッドで並列化するためのフラグ
  * `extras`: 追加のキーワード引数

# 戻り値

  * `algorithm`: Metropolisインスタンス
