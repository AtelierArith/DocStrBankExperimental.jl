```
set_vector!(
    daf::DafWriter,
    axis::AbstractString,
    name::AbstractString,
    vector::Union{StorageScalar, StorageVector};
    [overwrite::Bool = false]
)::Nothing
```

`daf`の特定の`axis`に対して、いくつかの`name`を持つベクトルプロパティを設定します。

指定された`vector`が実際に[`StorageScalar`](@ref)である場合、保存されたベクトルはこの値で満たされます。

最初に、`axis`が`daf`に存在すること、プロパティ名が`name`でないこと、そして`vector`が適切な長さであることを確認します。`overwrite`（デフォルト）でない場合、これにより`axis`に対して`name`ベクトルが存在しないことも確認されます。
