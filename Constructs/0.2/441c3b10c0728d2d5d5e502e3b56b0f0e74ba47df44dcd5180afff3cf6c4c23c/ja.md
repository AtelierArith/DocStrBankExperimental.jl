```
Singleton(T) -> Construct{T}
Singleton(instance::T) -> Construct{T}
```

シングルトン型のための空の構造体を定義します。

これは `Nothing` と `Missing` のデフォルトコンストラクタです。

# 例

```jldoctest
julia> serialize(missing)
UInt8[]

julia> deserialize(Singleton(pi), UInt8[])
π = 3.1415926535897...
```
