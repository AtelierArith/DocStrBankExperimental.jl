```
function unsafe_fbinomial(n::Int, k::Int)
```

fbinomialと同様ですが、境界チェックがありません。したがって、`n < 0`または`n > _nmax`または`k < 0`または`k > n`の場合、結果は未定義です。ウィグナー記号の計算において、数学的に`unsafe_fbinomial(n, k)`は常に安全であることが保証されています。
