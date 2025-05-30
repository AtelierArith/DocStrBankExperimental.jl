```
pCN(noise::NoiseGrid, ρ; reset=true, rng = Xorshifts.Xoroshiro128Plus(rand(UInt64)))
```

`noise` と追加のエントロピーを用いて相関 ρ を持つ新しいが相関のあるノイズプロセスを作成します。この更新は、メトロポリス・ヘイスティングスアルゴリズムで提案分布として使用できるウィーナー（またはノイズプロセス）軌道の空間における自己回帰プロセスを定義します（しばしば「前処理されたクランク–ニコルソン法」と呼ばれます）。

外部リンク

  * [ウィキペディアの前処理されたクランク–ニコルソンアルゴリズム](https://en.wikipedia.org/wiki/Preconditioned_Crank%E2%80%93Nicolson_algorithm)
