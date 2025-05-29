```
abstract type AbstractIteratedIntegralAlgorithm end
```

反復積分のシミュレーションのためのアルゴリズムの抽象型です。

```jldoctest; setup=:(using InteractiveUtils; using LevyArea)
julia> subtypes(AbstractIteratedIntegralAlgorithm)
4-element Vector{Any}:
 Fourier
 Milstein
 MronRoe
 Wiktorsson
```
