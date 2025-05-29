```
injectivity_radius(M::AbstractManifold)
```

全ての点 `p` に対する射影半径 `injectivity_radius(M,p)` の下限。

```
injectivity_radius(M::AbstractManifold, p)
```

全ての接ベクトルが距離 $d$ より短い場合に [`exp(M, p, X)`](@ref exp(::AbstractManifold, ::Any, ::Any)) が単射であるような距離 $d$ を返します（すなわち、逆が存在します）。

```
injectivity_radius(M::AbstractManifold[, x], method::AbstractRetractionMethod)
injectivity_radius(M::AbstractManifold, x, method::AbstractRetractionMethod)
```

点 `p` が提供されている場合はその点に対して、そうでない場合は全ての多様体の点に対して、全ての接ベクトルが距離 $d$ より短い場合に [`retract(M, p, X, method)`](@ref retract(::AbstractManifold, ::Any, ::Any, ::AbstractRetractionMethod)) が単射であるような距離 $d$。

異なる射影法に基づいてディスパッチするためには、あなたの射影 `R` に対して `_injectivity_radius(M[, p], m::T)` を実装するか、指数写像のために特に `injectivity_radius_exp(M[, p])` を実装してください。デフォルトでは、点 `p` を持つバリアントは、デフォルト（`p` なし）を下限として呼び出すことができると仮定します。
