```
struct Benchmark
    samples::Vector{Sample}
    ...more fields may be added...
end
```

完全なベンチマーク結果を表す構造体。[`@be`](@ref)によって返されます。

将来的に、サンプル特有の情報以外を表すために、さらにフィールドが追加される可能性があります。

関数 `minimum` と `maximum` は `Benchmark` オブジェクトに対してフィールド単位で定義されており、[`Sample`](@ref) を返します。Julia 1.9 以降では、関数 `Statistics.median`、`Statistics.mean`、および `Statistics.quantile` も `Benchmark` オブジェクトに対してフィールド単位で定義されており、`Sample` を返します。

```jldoctest; filter = [r"\d\d?\d?\.\d{3} [μmn]?s( \(.*\))?"=>s"RES", r"\d+ (sample|evaluation)s?"=>s"### \1"]
julia> @be eval(:(for _ in 1:10; sqrt(rand()); end))
Benchmark: 15 samples with 1 evaluation
 min    4.307 ms (3608 allocs: 173.453 KiB, 92.21% compile time)
 median 4.778 ms (3608 allocs: 173.453 KiB, 94.65% compile time)
 mean   6.494 ms (3608 allocs: 173.453 KiB, 94.15% compile time)
 max    12.021 ms (3608 allocs: 173.453 KiB, 95.03% compile time)

julia> minimum(ans)
4.307 ms (3608 allocs: 173.453 KiB, 92.21% compile time)
```
