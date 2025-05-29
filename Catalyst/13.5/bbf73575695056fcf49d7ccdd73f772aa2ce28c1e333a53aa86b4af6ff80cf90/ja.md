```
incidencemat(rn::ReactionSystem; sparse=false)
```

`rn`のインシデンス行列を計算します。詳細は[`reactioncomplexes`](@ref)を参照してください。

注意:

  * 同じスパース性を仮定した場合、将来の呼び出しも高速になるように`rn`にキャッシュされます。
