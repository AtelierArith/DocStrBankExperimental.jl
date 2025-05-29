```
is_synthetic(p::PointRecord)
is_synthetic(points, inds = :)
```

ポイントがレーザーパルスによる直接測定ではなく、「合成」手段（例：フォトグラメトリ）を通じて取得されたとマークされているかどうかを確認します。

参照： [`PointRecord`](@ref), [`classification`](@ref), [`is_key_point`](@ref), [`is_overlap`](@ref), [`is_withheld`](@ref)
