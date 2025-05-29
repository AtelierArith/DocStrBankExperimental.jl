```
reverse_sense(::Val{T}) where {T}
```

与えられた (不)等号シンボル `T` に対して、反対の (不)等号シンボルを持つ新しい `Val` オブジェクトを返します。

この関数は JuMP 拡張での使用を目的としています。

## 例

```jldoctest
julia> reverse_sense(Val(:>=))
Val{:<=}()
```
