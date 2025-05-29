```
@sleefmath expr
```

変換された式を実行します。これは、厳密なIEEEセマンティクスに違反する可能性のある関数を呼び出し、[SLEEFPirates](https://github.com/JuliaSIMD/SLEEFPirates.jl)パッケージを使用します。これにより、コンパイラは厳密なIEEEセマンティクスでは不可能なSIMD命令やその他の最適化を使用できるようになります。

このマクロは、ループやブロードキャストされた式内でのみ効果的です。forループで使用する場合、効果的にするためには、しばしば`@simd ivdep for`ループと`@inbounds`の使用が必要です。ブロードキャストされた式の場合、[FastBroadcast](https://github.com/YingboMa/FastBroadcast.jl)パッケージの`@..`を使用することが便利です。

# 例

```julia-repl
julia> @sleefmath exp(sin(3.0))
1.151562836514535

julia> xs = rand(10^6); ys = similar(xs);

julia> using BenchmarkTools, FastBroadcast

julia> @btime @.. $ys = @sleefmath exp(sin($xs));
  3.708 ms (0 allocations: 0 bytes)

julia> @btime @.. $ys = exp(sin($xs));
  10.265 ms (0 allocations: 0 bytes)

julia> @btime (@simd ivdep for n ∈ eachindex($xs); @inbounds $ys[n] = @sleefmath exp(sin($xs[n])); end);
  3.719 ms (0 allocations: 0 bytes)
```
