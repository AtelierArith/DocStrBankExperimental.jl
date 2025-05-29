```
fromspec(::Type{DataCollection}, spec::Dict{String, Any};
         path::Union{String, Nothing}=nothing, mod::Module=Base.Main)
```

`spec`から`DataCollection`を作成します。

`path`と`mod`のキーワードは、DataCollectionの対応するフィールドの値として使用されます。
