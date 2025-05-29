```
refine!(mdbm::MDBM_Problem{fcT,N,Nf,Nc,t01T,t11T,IT,FT,aT}; directions::Vector{T}=collect(Int64,1:N)) where N where Nf where Nc where T<:Integer
```

提供された `directions` に沿って軸の解像度を2倍にし、それに応じて `ncubes` を半分にします。

# 例

```jldoctest
julia> refine!(mymdbm)
julia> refine!(mymdbm,[1,1,2])
```
