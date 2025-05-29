```
discrete_observation_times(Q, k=2^10, t=0.0)
```

𝐑(t) = exp(t𝐐) を Yoon & Shanthikumar (1989, p. 181) の P₄ を使用して近似します。ここで、Rᵢⱼ は状態 𝑗 から状態 𝑖 に時間 𝑡 で到達する確率です。k パラメータは効率のために2の累乗に設定する必要があります。

この方法は、k ≤ t * getmaxrate(Q) の場合、正確でない結果を与える可能性があります！
