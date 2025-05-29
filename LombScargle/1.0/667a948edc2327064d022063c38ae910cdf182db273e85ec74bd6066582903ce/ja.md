```
findmaxfreq(p::Periodogram, [interval::AbstractVector{Real}], threshold::Real=findmaxpower(p))
```

周期グラム `p` で最も高いパワーを持つ周波数の配列を返します。スカラー実数引数 `threshold` が提供されている場合、`threshold` 以上のパワーを持つ周波数を返します。検索を狭い周波数範囲に制限したい場合は、2 番目の引数として区間の端点を持つベクトルを渡してください。
