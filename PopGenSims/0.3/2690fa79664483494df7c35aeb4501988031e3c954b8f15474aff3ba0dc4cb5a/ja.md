```
append(data::PopData, data2::PopData)
```

`data2`の行を`data`の末尾に追加します。これにより、両方の`PopData`オブジェクトに存在するサンプルが結合され、新しい`PopData`オブジェクトが返されます。**注意**：これは単純な追加であり、2つの`PopData`オブジェクトが同一のロキを持っていない場合、`PopData`が破損するリスクがあります。

**例**

```
julia> cats = @nanycats
PopData{Diploid, 9 Microsatellite Loci}
  Samples: 237
  Populations: 17


julia> purrfect_pairs = cross(cats, "N200", "N7", generation = "F1")
PopData{Diploid, 9 Microsatellite Loci}
  Samples: 100
  Populations: 1

julia> merged_cats = append(cats, purrfect_pairs)
PopData{Diploid, 9 Microsatellite Loci}
  Samples: 337
  Populations: 18
```
