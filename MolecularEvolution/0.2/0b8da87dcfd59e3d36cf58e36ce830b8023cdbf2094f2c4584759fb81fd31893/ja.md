```
brents_method_minimize(f, a::Real, b::Real, transform, t::Real; ε::Real=sqrt(eps()))
```

最適化のためのブレント法。

区間 (a,b) に単一の局所最小値を持つ関数 f が与えられた場合、ブレント法は f を 2tol と 3tol の間の精度で最小化する x 値の近似を返します。ここで、tol は相対的および絶対的な許容誤差の組み合わせであり、tol := ε|x| + t です。ε は `2*eps` より小さくてはならず、できれば `sqrt(eps)` よりもあまり小さくない方が望ましいです。eps はここで倍精度の機械イプシロンとして定義されています。t は正である必要があります。

この手法は、ゴールデンセクションサーチの安定性と、特定の条件下での超線形収束を持つ連続放物補間の特性を組み合わせています。この手法は、フィボナッチサーチよりも収束が遅くなることはほとんどなく、十分に良好な f に対しては、収束が超線形であることが期待でき、その次数は通常少なくとも 1.3247 以上です。

# 例

```jldoctest
julia> f(x) = exp(-x) - cos(x)
f (generic function with 1 method)

julia> m = brents_method_minimize(f, -1, 2, identity, 1e-7)
0.5885327257940255
```

出典: Richard P. Brent, "Algorithms for Minimization without Derivatives" (1973). 第5章。
