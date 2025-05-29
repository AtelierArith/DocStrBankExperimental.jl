```
SingleComponentMetropolisHastings(proposal, x0, n, burnin, islog)
```

[`bayesianupdating`](@ref) に渡され、`x0` から始まる単一成分メトロポリス・ヘイスティングスアルゴリズムを実行します。提案分布 `proposal` を持つ単変量です。マルコフ連鎖の `burnin` ステップを実行し、サンプルを破棄した後に `n` サンプルを生成します。フラグ `islog` は、[`bayesianupdating`](@ref) メソッドに渡される事前および尤度関数がすでに対数として与えられているかどうかを指定します。

代替コンストラクタ

```julia
    SingleComponentMetropolisHastings(proposal, x0, n, burnin)  # `islog` = true
```
