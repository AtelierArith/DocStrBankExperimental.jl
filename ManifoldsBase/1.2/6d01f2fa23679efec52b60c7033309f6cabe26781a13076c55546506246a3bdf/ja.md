```
inverse_retract!(M::AbstractManifold, X, p, q[, method::AbstractInverseRetractionMethod])
```

点 `p` と `q` の [`AbstractManifold`](@ref) `M` 上の逆射影を計算します。これは、より安価で近似的な [`log`](@ref) 算術マップのバージョンです。結果は `X` に保存されます。

逆射影法は最後の引数で指定でき、デフォルトは [`default_inverse_retraction_method`](@ref)`(M)` です。利用可能な方法については、各多様体のドキュメントを参照してください。

また、[`retract!`](@ref) も参照してください。
