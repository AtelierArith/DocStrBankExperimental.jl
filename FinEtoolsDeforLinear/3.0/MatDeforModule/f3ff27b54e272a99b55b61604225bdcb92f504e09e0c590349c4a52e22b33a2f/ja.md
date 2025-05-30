```
stressvtot!(::Type{DeforModelRed2DAxisymm}, t::Matrix{T}, v::Vector{T}) where {T}
```

4ベクトルを3x3応力成分（テンソル）の行列に変換します。

4ベクトルを*対称*な3x3応力成分（テンソル）の行列に変換します。

応力ベクトルの成分は次のように順序付ける必要があります：sigmax, sigmay, sigmaz, tauxy。
