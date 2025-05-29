```
ApproximatePermutationTest([rng::AbstractRNG,] x::Vector, y::Vector, f::Function, n::Int)
```

帰無仮説 `f(x)` が `f(y)` と等しいという仮説のための置換検定（別名：ランダム化検定）を実行します。`factorial(length(x)+length(y))` の中から `n` の置換がランダムにサンプリングされます。ランダム数生成器は、最初の引数としてオプションで渡すことができます。デフォルトの生成器は `Random.default_rng()` です。
