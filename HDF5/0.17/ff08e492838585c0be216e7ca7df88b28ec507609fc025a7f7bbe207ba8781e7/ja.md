```
create_attribute(parent::Union{File,Object}, name::AbstractString, dtype::Datatype, space::Dataspace)
create_attribute(parent::Union{File,Object}, name::AbstractString, data)
```

オブジェクト `parent` に `name` という新しい [`Attribute`](@ref) オブジェクトを作成します。属性の `Datatype` と `Dataspace` を指定するか、データを提供することで作成できます。データは書き込まれないことに注意してください: データを書き込むには [`write_attribute`](@ref) を使用してください。
