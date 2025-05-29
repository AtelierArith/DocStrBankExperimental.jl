```
size(hmm, [dim]) -> Int | Tuple
```

`hmm`の状態数と観測の次元を返します。

**例**

```jldoctest
using Distributions, HMMBase
hmm = HMM([0.9 0.1; 0.1 0.9], [Normal(0,1), Normal(10,1)])
size(hmm)
# 出力
(2, 1)
```
