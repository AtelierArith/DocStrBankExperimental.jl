```
function ParamDict(type)
    Union{Dict{String, Array{T}}, Dict{String, Vector{T}}} where T <: type
end
```

モデルパラメータの辞書の型コンストラクタで、名前によって導関数関数に渡されます。これにより、ベクトルパラメータ（およびベクトルとして書かれたスカラー）と、拡散配列のような行列値パラメータの両方を渡すことができます。
