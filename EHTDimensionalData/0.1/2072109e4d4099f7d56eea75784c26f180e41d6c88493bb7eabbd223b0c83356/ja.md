```
append(dataset::DimStack, array::DimArray)::DimStack
```

指定された DimStack データセットに DimArray データを追加します。DimStack に同じキーを持つ配列がすでに存在する場合、新しく追加された配列によって上書きされます。新しく追加された `DimArray` または `DimStack` データセットから継承された他の `DimArray` は、元のものとプログラム的に区別できません。

# 例

```julia
julia> # 例えば、`ds::DimStack` に `:newcol` という名前の `da::DimArray` を追加したとします。
julia> newds = append(ds, da)

julia> # newds は新しく形成された `DimStack` です。なぜなら `DimStack` は不変の `NamedTuple` を使用するからです。
julia> newds == ds
false

julia> # 追加された `DimArray` または他の `DimArray` はプログラム的に区別できません。
julia> newds[:newcol] === da
true
julia> newds[:orgcol] === ds[:orgcol]
true
```
