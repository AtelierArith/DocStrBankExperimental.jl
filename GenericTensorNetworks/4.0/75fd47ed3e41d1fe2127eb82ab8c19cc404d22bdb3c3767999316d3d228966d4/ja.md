```
hamming_distribution(S, T)
```

ペアワイズハミング距離の分布を計算します。これは次のように定義されます：

$$
c(k) := \sum_{\sigma\in S, \tau\in T} \delta({\rm dist}(\sigma, \tau), k)
$$

ここで、$\delta$は2つの引数が等しい場合に1を返し、そうでない場合は0を返す関数であり、${\rm dist}$はハミング距離関数です。

カウントをベクトルとして返します。
