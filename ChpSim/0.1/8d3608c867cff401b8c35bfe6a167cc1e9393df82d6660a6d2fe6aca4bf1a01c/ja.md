```
measure!(state, qubit; rng=GLOBAL_RNG, bias=0.5)
```

Z基底で測定を行い、結果を返します。キュービットが重ね合わせにあった場合は、ランダムな結果を選択し、状態を更新します。

# 引数

  * `qubit::Int`: 測定するキュービットのインデックス。
  * `rng::AbstractRNG`: 使用する乱数生成器。
  * `bias::Real`: ランダムに1を測定する人工的な確率。
