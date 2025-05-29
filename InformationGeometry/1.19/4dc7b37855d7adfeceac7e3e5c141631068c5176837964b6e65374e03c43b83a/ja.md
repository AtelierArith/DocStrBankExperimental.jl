```
LinkParameters(DM::AbstractDataModel, Linked::Union{AbstractVector{<:Bool},AbstractVector{<:Int}}, MainIndBefore::Int=findfirst(Linked); kwargs...)
```

モデルを埋め込むことで、`Linked[i] == true` であるすべてのコンポーネント `i` が、コンポーネント `MainIndBefore` に対応するパラメータにリンクされます。`Linked` は `String` でも構いません：これにより、対応するパラメータ名に `Linked` が含まれている場合に `true` となる `BitVector` が作成されます。
