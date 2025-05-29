```
(ds::KeyedDataset)(key) -> KeyedDataset
```

[`KeyedDataset`](@ref) のサブセットを選択またはフィルタリングするためのコラブル構文です。

# 例

```jldoctest
julia> using AxisKeys; using AxisSets: KeyedDataset, flatten;

julia> ds = KeyedDataset(
           flatten([
               :g1 => [
                   :a => KeyedArray(zeros(3); time=1:3),
                   :b => KeyedArray(ones(3, 2); time=1:3, loc=[:x, :y]),
                ],
                :g2 => [
                    :a => KeyedArray(ones(3); time=1:3),
                    :b => KeyedArray(zeros(3, 2); time=1:3, loc=[:x, :y]),
                ]
            ])...
       );

julia> collect(keys(ds(:__, :a).data))
2-element Vector{Tuple}:
 (:g1, :a)
 (:g2, :a)

julia> collect(keys(ds(:g1, :__).data))
2-element Vector{Tuple}:
 (:g1, :a)
 (:g1, :b)
```
