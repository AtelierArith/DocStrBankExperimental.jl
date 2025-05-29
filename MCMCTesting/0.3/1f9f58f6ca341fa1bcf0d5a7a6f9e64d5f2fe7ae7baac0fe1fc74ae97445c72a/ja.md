```
markovchain_transition(rng, model, kernel, θ, y)
```

`y`を条件とした`model`の事後分布に対して、前の状態`θ`で`kernel`の単一マルコフ連鎖遷移を実行します。

# 引数

  * `rng::Random.AbstractRNG`: 擬似乱数生成器。
  * `model`: `y`を条件とした事後分布`p(θ|y)`を形成するモデル。
  * `θ`: マルコフ連鎖の前の状態。
  * `y`: 条件とするデータ。

# 戻り値

  * `θ′`: マルコフ連鎖の次の状態。
