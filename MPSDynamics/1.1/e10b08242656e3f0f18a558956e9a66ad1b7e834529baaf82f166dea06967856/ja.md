```
TwoSiteObservable(name,op1,op2,sites1=nothing,sites2=nothing)
```

演算子 `op1` と `op2` の局所期待値を計算します。`op1` は sites1 に作用し、`op2` は sites2 に作用します。これは、`runsim` 関数の obs および convobs パラメータとして使用される複数サイトの観測量を定義するために使用されます。
