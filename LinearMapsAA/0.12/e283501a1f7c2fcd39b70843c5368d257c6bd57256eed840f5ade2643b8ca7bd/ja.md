```
A = LinearMapAA(L::LinearMap ; ...)
```

`LinearMap` に基づいて `LinearMapAM` または `LinearMapAO` のコンストラクタ。

# オプション

  * `prop::NamedTuple = NamedTuple()`; フィールド `_lmap`, `_prop`, `_idim`, `_odim` を含めることはできません
  * `T::Type = eltype(L)`
  * `idim::Dims = (size(L,2),)`
  * `odim::Dims = (size(L,1),)`
  * `operator::Bool` デフォルト: `false` もし `idim` と `odim` が両方とも 1D の場合。

出力 `A` は `operator` が `true` の場合は `LinearMapAO` であり、そうでなければ `LinearMapAM` です。
