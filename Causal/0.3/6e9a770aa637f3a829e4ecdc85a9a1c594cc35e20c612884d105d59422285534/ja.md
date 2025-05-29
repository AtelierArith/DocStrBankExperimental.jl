```julia
connect!(outpin, inpin)

```

`outpin`を`inpin`に接続します。接続されると、`outpin`に入れられた要素はすべて`inpin`にも入れられます。

# 例

```jldoctest
julia> op, ip = Outpin(), Inpin();

julia> l = connect!(op, ip)
Link(state:open, eltype:Float64, isreadable:false, iswritable:false)

julia> l in op.links
true

julia> ip.link === l
true
```
