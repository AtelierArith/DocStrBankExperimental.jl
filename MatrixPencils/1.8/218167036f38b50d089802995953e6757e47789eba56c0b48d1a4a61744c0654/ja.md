```
eigselect2(evr, evc, sdeg, evref, disc) -> (γ, evrupd, evcupd)
```

与えられた実固有値のセット `evr` と複素固有値のセット `evc` から、固有値のペア `γ[1]` と `γ[2]` を選択します。選択された固有値は、参照値 `evref` に最も近いものです。複素固有値のペアは常に選択されますが、`evc = missing` の場合は実固有値のペアが選択されます。結果として得られる `evrupd` には `evr` からの残りの実固有値が含まれ、結果として得られる `evcupd` には `evc` からの残りの複素固有値が含まれます。希望する安定度 `sdeg` が欠けている場合、デフォルト値 `sdeg = sdegdef` が使用されます。ここで、`sdegdef = -0.05` は `disc = false` の場合、`sdegdef = .95` は `disc = true` の場合です。`evc = missing` で `evr` に少なくとも2つの固有値が含まれている場合、`γ[1]` と `γ[2]` は `evref` に最も近い2つの実固有値が選ばれます。`evc = missing` で `evr` に1つの値しか含まれていない場合、`γ[1] = evr` および `γ[2] = sdeg` となります。`evr = missing`、`evc = missing` で `disc = false` の場合、`γ[1] = sdeg + im*imag(evref)` および `γ[2] = sdeg - im*imag(evref)` となります。`evr = missing`、`evc = missing` で `disc = true` の場合、`γ[1] = sdeg/abs(evref))*evref[1]` および `γ[2] = sdeg/abs(evref))*evref[2]` となります。
