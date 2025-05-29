```
sortBasis(bs::Union{AbstractArray{<:CompositeGTBasisFuncs{T, D}}, 
                    Tuple{Vararg{CompositeGTBasisFuncs{T, D}}}}; 
          roundAtol::Real=getAtolVal(T)) where {T, D} -> 
Vector{<:CompositeGTBasisFuncs{T, D}}
```

基底関数をソートします。`roundAtol`は、各`CompositeGTBasisFuncs`に格納されたパラメータを比較して「等しい」と見なすかどうかを決定するための絶対近似許容誤差を指定します。`NaN`に設定されている場合、比較中に近似は行われません。
