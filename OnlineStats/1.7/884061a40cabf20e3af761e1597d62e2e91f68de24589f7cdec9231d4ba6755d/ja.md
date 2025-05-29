```
LogSumExp(T::Type = Float64)
```

非常に小さい（または非常に大きい）正の数に対しては、アンダーフロー（またはオーバーフロー）を避けるために、各 `x` 自体の代わりに各 `log(x)` を保存することが一般的です。`LogSumExp` はこの表現で値を受け取り、それらを加算し、同じ表現で結果を返します。

参照: [https://www.nowozin.net/sebastian/blog/streaming-log-sum-exp-computation.html](https://www.nowozin.net/sebastian/blog/streaming-log-sum-exp-computation.html)

# 例

```
x = randn(1000)

fit!(LogSumExp(), x)

log(sum(exp.(x))) # 非常に近いはず
```
