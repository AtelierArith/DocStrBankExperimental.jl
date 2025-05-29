```
log(M::AbstractManifold, p, q)
```

点 `p` における点 `q` の対数写像を [`AbstractManifold`](@ref) `M` で計算します。対数写像は [`exp`](@ref) 指数写像の逆です。対数写像は全体的に定義されていない場合があることに注意してください。

また、[`inverse_retract`](@ref) も参照してください。
