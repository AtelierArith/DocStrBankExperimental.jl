```
reflect(M, f, x; kwargs...)
reflect!(M, q, f, x; kwargs...)
```

多様体 `M` の点 `f(x)` での点 `x` を反射します。関数 $f: \mathcal M → \mathcal M$ によって与えられます。

$$
    \operatorname{refl}_f(x) = \operatorname{refl}_{f(x)}(x),
$$

結果を `q` に計算します。

さらに [`reflect`](@ref reflect(M::AbstractManifold, p, x))`(M,p,x)` も参照してください。キーワードもそこに渡されます。
