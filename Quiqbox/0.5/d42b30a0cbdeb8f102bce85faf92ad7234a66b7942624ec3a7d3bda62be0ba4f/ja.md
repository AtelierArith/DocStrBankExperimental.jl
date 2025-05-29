```
sortBasisFuncs(bs::AbstractArray{<:FloatingGTBasisFuncs{T, D}}, 
               groupCenters::Bool=false; roundAtol::Real=getAtolVal(T)) where {T, D} -> 
Vector
```

`FloatingGTBasisFuncs`をソートします。`groupCenters = true`の場合、関数は同じ中心座標を持つ要素がグループ化された`Vector{<:Vector{<:FloatingGTBasisFuncs}}`を返します。`roundAtol`は、中心座標を比較して「等しい」と見なすかどうかを決定するための絶対近似許容誤差を指定します。`NaN`に設定すると、比較中に近似は行われません。
