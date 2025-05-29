```
stressvtot!(::Type{DeforModelRed2DStrain}, t::Matrix{T}, v::Vector{T}) where {T}
```

ベクトルを2x2の応力成分の行列（対称テンソル）に変換します。

もし`v`が4つのエントリを持つ場合、`t[3,3]`の行列エントリも設定されます。

応力ベクトル成分は次のように順序付ける必要があります：sigmax, sigmay, tauxy, sigmaz。これは平面ひずみモデルの縮小に使用される順序です。
