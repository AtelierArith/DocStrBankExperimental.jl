# LazyArrays.jl

[![Dev](https://img.shields.io/badge/docs-dev-blue.svg)](https://juliaarrays.github.io/LazyArrays.jl/dev) [![Build Status](https://github.com/JuliaArrays/LazyArrays.jl/workflows/CI/badge.svg)](https://github.com/JuliaArrays/LazyArrays.jl/actions) [![codecov](https://codecov.io/gh/JuliaArrays/LazyArrays.jl/branch/master/graph/badge.svg)](https://codecov.io/gh/JuliaArrays/LazyArrays.jl) [![pkgeval](https://juliahub.com/docs/General/LazyArrays/stable/pkgeval.svg)](https://juliaci.github.io/NanosoldierReports/pkgeval_badges/report.html)

Juliaにおける遅延配列と線形代数

このパッケージは、`vcat`、`hcat`、および乗算のような配列操作の遅延アナログをサポートします。これは、反復ソルバーのための行列フリー法の実装に役立ちます。

このパッケージは高性能を念頭に設計されているため、`copyto!`やブロードキャスティングのような多くの操作において、Baseの非遅延アナログよりも優れた性能を発揮するはずです。`getindex`のように、追加の計算が必要なために本質的に遅くなる操作もあります。Baseのアナログよりも著しく遅い例があれば、問題を報告してください。

## 遅延操作

関数呼び出し `f(x,y,z...)` の遅延表現を構築するには、コマンド `applied(f, x, y, z...)` を使用します。これにより、操作を表す通常は `Applied` 型の未具現化オブジェクトが返されます。そのオブジェクトを具現化するには、通常 `f(x,y,z...)` を呼び出すのと同等の `materialize` を呼び出します。マクロ `@~` がショートハンドとして利用可能です：

```julia
julia> using LazyArrays, LinearAlgebra

julia> applied(exp, 1)
Applied(exp,1)

julia> materialize(applied(exp, 1))
2.718281828459045

julia> materialize(@~ exp(1))
2.718281828459045

julia> exp(1)
2.718281828459045
```

`@~` は、トップレベルの式だけでなく、サブ式を `applied` 呼び出しでラップすることに注意してください。これにより、サブ式の遅延適用がまだ実装されていない場合に `MethodError` が発生することがあります。例えば、

```julia
julia> @~ Vector(1:10) .* ones(10)'
ERROR: MethodError: ...

julia> A = Vector(1:10); B = ones(10); (@~ sum(A .* B')) |> materialize
550.0
```

遅延操作の利点は、簡略化を使用してインプレースで具現化できることです。例えば、遅延適用オブジェクトを使用して `α*A*x + β*y` の形のBLASライクな行列-ベクトル操作を行うことが可能です：

```julia
julia> A = randn(5,5); b = randn(5); c = randn(5); d = similar(c);

julia> d .= @~ 2.0 * A * b + 3.0 * c # gemv!を呼び出します
5-element Array{Float64,1}:
 -2.5366335879717514
 -5.305097174484744  
 -9.818431932350942  
  2.421562605495651  
  0.26792916096572983

julia> 2*(A*b) + 3c
5-element Array{Float64,1}:
 -2.5366335879717514
 -5.305097174484744  
 -9.818431932350942  
  2.421562605495651  
  0.26792916096572983

julia> function mymul(A, b, c, d) # ベンチマーク用に関数を定義する必要があります
       d .= @~ 2.0 * A * b + 3.0 * c
       end
mymul (generic function with 1 method)

julia> @btime mymul(A, b, c, d) # gemv!を呼び出します
  77.444 ns (0 allocations: 0 bytes)
5-element Array{Float64,1}:
 -2.5366335879717514
 -5.305097174484744  
 -9.818431932350942  
  2.421562605495651  
  0.26792916096572983

julia> @btime 2*(A*b) + 3c; # gemv!を呼び出しません
  241.659 ns (4 allocations: 512 bytes)
```

これは、可能な限りBLAS呼び出しに降下する逆行列にも適用されます：

```julia
julia> A = randn(5,5); b = randn(5); c = similar(b);

julia> c .= @~ A \ b
5-element Array{Float64,1}:
 -2.5366335879717514
 -5.305097174484744  
 -9.818431932350942  
  2.421562605495651  
  0.26792916096572983
```

## 遅延配列

しばしば、行列の遅延実現が必要であり、これは `ApplyArray` を介してサポートされています。例えば、次のように遅延行列指数関数を作成します：

```julia
julia> E = ApplyArray(exp, [1 2; 3 4])
2×2 ApplyArray{Float64,2,typeof(exp),Tuple{Array{Int64,2}}}:
  51.969   74.7366
 112.105  164.074 
```

遅延行列指数関数は、例えば、インプレースの行列指数関数*ベクトルに便利です：

```julia
julia> b = Vector{Float64}(undef, 2); b .= @~ E*[4,4]
2-element Array{Float64,1}:
  506.8220830628333
 1104.7145995988594
```

これが機能しますが、実際には最適化されていません（まだ）。 

他のオプションには、特別な実装があり、これにより高速化されます。いくつかの例を示します。

### 連結

遅延 `vcat` と `hcat` は、実際にメモリを割り当てることなくベクトルの連結を表現でき、ベクトルの割り当てなしの人口に対して高速な `copyto!` をサポートします。

```julia
julia> using BenchmarkTools

julia> A = ApplyArray(vcat,1:5,2:3) # 割り当てなし
7-element ApplyArray{Int64,1,typeof(vcat),Tuple{UnitRange{Int64},UnitRange{Int64}}}:
 1
 2
 3
 4
 5
 2
 3

julia> Vector(A) == vcat(1:5, 2:3)
true

julia> b = Array{Int}(undef, length(A)); @btime copyto!(b, A);
  26.670 ns (0 allocations: 0 bytes)

julia> @btime vcat(1:5, 2:3); # メモリ作成のために2倍の時間がかかります
  43.336 ns (1 allocation: 144 bytes)
```

同様に、`hcat` の遅延アナログもあります：

```julia
julia> A = ApplyArray(hcat, 1:3, randn(3,10))
3×11 ApplyArray{Float64,2,typeof(hcat),Tuple{UnitRange{Int64},Array{Float64,2}}}:
 1.0   1.16561    0.224871  -1.36416   -0.30675    0.103714    0.590141   0.982382  -1.50045    0.323747  -1.28173  
 2.0   1.04648    1.35506   -0.147157   0.995657  -0.616321   -0.128672  -0.671445  -0.563587  -0.268389  -1.71004  
 3.0  -0.433093  -0.325207  -1.38496   -0.391113  -0.0568739  -1.55796   -1.00747    0.473686  -1.2113     0.0119156

julia> Matrix(A) == hcat(A.args...)
true

julia> B = Array{Float64}(undef, size(A)...); @btime copyto!(B, A);
  109.625 ns (1 allocation: 32 bytes)

julia> @btime hcat(A.args...); # メモリ作成のために2倍の時間がかかります
  274.620 ns (6 allocations: 560 bytes)
```

### クロネッカー積

完全な配列を構築することなく、配列のクロネッカー積を表現できます：

```julia
julia> A = randn(2,2); B = randn(3,3);

julia> K = ApplyArray(kron,A,B)
6×6 ApplyArray{Float64,2,typeof(kron),Tuple{Array{Float64,2},Array{Float64,2}}}:
 -1.08736   -0.19547   -0.132824   1.60531    0.288579    0.196093 
  0.353898   0.445557  -0.257776  -0.522472  -0.657791    0.380564 
 -0.723707   0.911737  -0.710378   1.06843   -1.34603     1.04876  
  1.40606    0.252761   0.171754  -0.403809  -0.0725908  -0.0493262
 -0.457623  -0.576146   0.333329   0.131426   0.165464   -0.0957293
  0.935821  -1.17896    0.918584  -0.26876    0.338588   -0.26381  

julia> C = Matrix{Float64}(undef, 6, 6); @btime copyto!(C, K);
  61.528 ns (0 allocations: 0 bytes)

julia> C == kron(A,B)
true
```

## ブロードキャスティング

Baseには `Broadcasting` という遅延ブロードキャストオブジェクトが含まれていますが、これは `AbstractArray` のサブタイプではありません。ここでは、配列インターフェースをサポートしながら `Broadcasting` の機能を再現する `BroadcastArray` を提供します。

```julia
julia> A = randn(6,6);

julia> B = BroadcastArray(exp, A);

julia> Matrix(B) == exp.(A)
true

julia> B = BroadcastArray(+, A, 2);

julia> B == A .+ 2
true
```

このような配列は、通常のブロードキャスティング式と `LazyArray` を組み合わせたマクロ `@~` を使用して作成することもできます：

```julia
julia> C = rand(1000)';

julia> D = LazyArray(@~ exp.(C))

julia> E = LazyArray(@~ @. 2 + log(C))

julia> @btime sum(LazyArray(@~ C .* C'); dims=1) # `@~`なしでは、1.438 ms (5 allocations: 7.64 MiB)
  74.425 μs (7 allocations: 8.08 KiB)
```
