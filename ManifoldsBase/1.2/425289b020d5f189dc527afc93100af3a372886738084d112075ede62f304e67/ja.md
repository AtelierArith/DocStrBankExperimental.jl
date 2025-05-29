```
log!(M::AbstractManifold, X, p, q)
```

点 `p` における基準点での点 `q` の対数写像を [`AbstractManifold`](@ref) `M` で計算します。結果は `X` に保存されます。対数写像は [`exp!`](@ref) 指数写像の逆です。対数写像はグローバルに定義されていない場合があることに注意してください。

さらに [`log`](@ref) と [`inverse_retract!`](@ref) も参照してください。
