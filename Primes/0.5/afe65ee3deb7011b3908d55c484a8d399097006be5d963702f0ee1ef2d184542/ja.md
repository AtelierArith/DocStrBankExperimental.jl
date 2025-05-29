```
isprime(x::BigInt, [reps = 25]) -> Bool
```

確率的素数判定テスト。`x` が高い確率で素数である場合は `true` を返し（擬似素数）、`x` が合成数（素数でない）である場合は `false` を返します。偽陽性率は約 `0.25^reps` です。`reps = 25` は暗号アプリケーションに対して安全と見なされます（Knuth, Seminumerical Algorithms）。

is*probably*prime は、GNU Multiple Precision Arithmetic Library (GMP) ライブラリの機能にアクセスするためのラッパーを提供する IntegerMathUtils モジュールから継承されています。

```julia
julia> isprime(big(3))
true
```
