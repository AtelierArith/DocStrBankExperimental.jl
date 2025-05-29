```
function bosonize(os::OpStrings{T1}, sites::Vector{Index{T2}}) where {T1 <: Number, T2}
```

元のオペレーター文字列を必要に応じてジョルダン-ウィグナー文字列で「ボソナイズ」した後、`OpStrings`を返します。詳細は[`bosonize`](@ref)を参照してください。
