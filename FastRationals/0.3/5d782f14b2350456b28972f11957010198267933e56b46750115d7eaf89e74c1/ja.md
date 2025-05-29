```
compactify(rational_to_compactify, radius_of_indifference)    

compactify(low=one_inteval_bound, high=other_interval_bound)
```

±`radius_of_indifference`の範囲内に存在するすべての有理数の中から、得られる区間は、(a) 分母が最小の大きさであり、(b) 分子が一意に与えられるか、利用可能なものの中で最小の大きさである有理数を一意に決定します。    

最初の形式は、丸め誤差のために不正確さに悩まされます。    

私たちは、源と結果の2つの有理数を大きさとして無関心です。次の算術演算でオーバーフローが起こりにくいため、計算にはコンパクト化された値を使用することを好みます。
