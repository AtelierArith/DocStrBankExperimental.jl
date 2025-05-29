```
findmaxperiod(p::Periodogram, [interval::AbstractVector{Real}], threshold::Real=findmaxpower(p))
```

周期図 `p` で最も高いパワーを持つ周期の配列を返します。スカラーの実引数 `threshold` が提供されている場合、`threshold` 以上のパワーを持つ周期を返します。検索を狭い周期範囲に制限したい場合は、2 番目の引数として区間の極値を持つベクトルを渡してください。
