```
terms_needed(dim, stepsize, eps, alg, norm)
```

与えられたノルムでの誤差が最大で `eps` になるように必要な近似和の項数を返します。これはウィーナー過程の次元 `dim`、現在のステップサイズ、および選択したアルゴリズムに依存します。

参照: [`AbstractIteratedIntegralAlgorithm`](@ref), [`AbstractErrorNorm`](@ref)

# 例

```jldoctest; setup=:(using LevyArea)
julia> h = 1/128;

julia> terms_needed(10, h, h^(3/2), Milstein(), MaxL2())
7
```

# 実装

新しいアルゴリズムは、[`errcoeff`](@ref) と [`convorder`](@ref) のみを実装すればよいです。
