```
inverse_retract(M::AbstractManifold, p, q)
inverse_retract(M::AbstractManifold, p, q, method::AbstractInverseRetractionMethod
```

点 `p` と `q` の [`AbstractManifold`](@ref) `M` 上の逆射影を計算します。これは、より安価で近似的な [`log`](@ref) 算術マップのバージョンです。

逆射影法は最後の引数で指定でき、デフォルトは [`default_inverse_retraction_method`](@ref)`(M)` です。特定の多様体における利用可能な逆射影については、対応する多様体のドキュメントを参照してください。

また、[`retract`](@ref) も参照してください。
