```
setsofsets_distances(a₊, a₋ [, distance]) → distances
```

`StateSpaceSet`のセット間の距離を計算します。ここで、`a₊, a₋`は`StateSpaceSet`のコンテナであり、返される距離は距離の辞書です。具体的には、`distances[i][j]`は、`a₊`の`i`キーのセットから`a₋`の`j`キーのセットまでの距離です。`a₋`から`a₊`への距離は全く計算されず、距離関数の対称性を仮定しています。

`distance`は[`set_distance`](@ref)に対して有効なものであれば何でも構いません。

コンテナ`a₊, a₋`は空であっても構いませんが、具体的に型付けされている必要があります。
