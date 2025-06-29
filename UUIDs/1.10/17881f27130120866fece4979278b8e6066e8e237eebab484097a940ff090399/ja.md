```
uuid4([rng::AbstractRNG]) -> UUID
```

RFC 4122で指定されたバージョン4（ランダムまたは擬似ランダム）のユニバーサルユニーク識別子（UUID）を生成します。

`uuid4`で使用されるデフォルトのrngは`GLOBAL_RNG`ではなく、引数なしで`uuid4()`を呼び出すたびにユニークな識別子が返されることが期待されます。重要なことに、`uuid4`の出力は、`Random.seed!(seed)`が呼ばれても繰り返されることはありません。現在（Julia 1.6時点）、`uuid4`はデフォルトのrngとして`Random.RandomDevice`を使用しています。ただし、これは将来的に変更される可能性のある実装の詳細です。

!!! compat "Julia 1.6"
    `uuid4`の出力は、Julia 1.6時点で`GLOBAL_RNG`に依存しません。


# 例

```jldoctest
julia> rng = MersenneTwister(1234);

julia> uuid4(rng)
UUID("7a052949-c101-4ca3-9a7e-43a2532b2fa8")
```
