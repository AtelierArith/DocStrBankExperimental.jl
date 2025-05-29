```
loglikelihood(hmm, observations; robust) -> Float64
```

モデルの下での観測の対数尤度を計算します。これは、前方フィルタの正規化係数の対数の合計として定義されます。

**出力**

  * `Float64`: モデルの下での観測シーケンスの対数尤度。

**例**

```jldoctest
using Distributions, HMMBase
hmm = HMM([0.9 0.1; 0.1 0.9], [Normal(0,1), Normal(10,1)])
loglikelihood(hmm, [0.15, 0.10, 1.35])
# output
-4.588183811489616
```
