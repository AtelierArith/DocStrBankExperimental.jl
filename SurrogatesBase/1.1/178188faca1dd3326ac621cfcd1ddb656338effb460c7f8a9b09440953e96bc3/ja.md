```
update!(s, new_xs::AbstractVector, new_ys::AbstractVector)
```

データ `new_ys` をポイント `new_xs` にサロゲート `s` に含め、すなわち新しいデータポイントを取り入れるためにサロゲート `s` を再フィットします。

サロゲート `s` が決定論的サロゲートである場合、`new_ys` は関数評価に対応し、`s` が確率的サロゲートである場合、`new_ys` は条件付き確率分布からのサンプルです。

`X` が行列である場合は、`update!(s, eachslice(X, dims = 2), new_ys)` を使用してください。
