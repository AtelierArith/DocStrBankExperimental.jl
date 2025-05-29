```
DETPFlash(; numphases = 2,
max_steps = 1e4*(numphases-1),
population_size =20,
time_limit = Inf,
verbose = false,
logspace = false,
equilibrium = :auto)
```

非反応性多成分フラッシュ問題を解決するためのメソッドで、ギブズ自由エネルギーのグローバルミニマムを微分進化によって見つけます。

ユーザーは、相の数 `numphases` を仮定する必要があります。実際の相の数が `numphases` より少ない場合、モデルは (a) 2つ以上の相で同一の組成を予測するか、(b) 総モル数が無視できる相を1つ予測します。実際の相の数が `numphases` より多い場合、熱力学的に不安定な解が予測されます。

最適化アルゴリズムは、`max_steps` 回の評価または `time_limit` 秒で停止します。

`equilibrium` キーワードを使用すると、相の探索を液-液平衡 (`equilibrium = :lle`) のみに制限できます。デフォルトでは液体と気体の相を検索します。
