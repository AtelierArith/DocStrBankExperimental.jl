```
function bosonize(opstr::OpString{T1},
                  sites::Vector{Index{T2}}) where {T1 <: Number, T2}
```

元のオペレーターを必要に応じてジョルダン-ウィグナー文字列で「ボソナイズ」した後に `OpString` を返します。詳細は [`bosonize`](@ref) を参照してください。
