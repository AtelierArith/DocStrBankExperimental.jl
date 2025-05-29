```
ChainedBonds{T<:Real,V<:AbstractVector{T}}
```

結合された結合を、結合長、結合角、およびねじれ角の系列としてバックボーンを格納するための怠惰な方法です。

# 例

```jldoctest
julia> backbone = Backbone(randn(Float32, 3, 660));

julia> bonds = ChainedBonds(backbone)
ChainedBonds{Float32, Vector{Float32}} with 659 bond lengths, 658 bond angles, and 657 torsion angles
```
