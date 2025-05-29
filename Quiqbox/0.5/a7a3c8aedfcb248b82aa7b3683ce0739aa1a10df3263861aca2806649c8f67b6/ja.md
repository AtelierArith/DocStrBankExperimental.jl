```
mergeBasisFuncsIn(bs::Union{AbstractVector{<:GTBasisFuncs{T, D}}, 
                            Tuple{Vararg{GTBasisFuncs{T, D}}}}; 
                  roundAtol::Real=NaN) where {T, D} -> 
Vector{<:GTBasisFuncs{T, D}}
```

複数の `FloatingGTBasisFuncs` を `bs` から `FloatingGTBasisFuncs{T, D, <:Any, <:Any, <:Any, ON}` にマージしようとします。ここで、`ON > 1` である場合に可能です。そして、結果として得られた基底コレクションを返します。マージが行われなかった場合、返されるコレクションは `bs` と同じですが、必ずしも同一ではありません。
