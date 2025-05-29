```
sample(X::LazySet, [m]::Int=1;
       [rng]::AbstractRNG=GLOBAL_RNG,
       [seed]::Union{Int,Nothing}=nothing)
```

集合からランダムサンプルを計算します。

### 入力

  * `X`    – 集合
  * `m`    – （オプション; デフォルト: 1）ランダムサンプルの数
  * `rng`  – （オプション、デフォルト: `GLOBAL_RNG`）乱数生成器
  * `seed` – （オプション、デフォルト: `nothing`）再シード用のシード

### 出力

`X` が空でない場合は `m` 要素のベクトルを返し、そうでない場合はエラーを返します。
