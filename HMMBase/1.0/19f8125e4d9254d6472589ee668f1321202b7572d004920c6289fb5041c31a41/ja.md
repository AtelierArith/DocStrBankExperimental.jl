```
nparams(hmm) -> Int
```

`hmm`の*自由*パラメータの数を返します。観測分布のパラメータはカウントしません。

**例**

```jldoctest
using Distributions, HMMBase
hmm = HMM([0.9 0.1; 0.1 0.9], [Normal(0,1), Normal(10,1)])
nparams(hmm)
# 出力
3
```
