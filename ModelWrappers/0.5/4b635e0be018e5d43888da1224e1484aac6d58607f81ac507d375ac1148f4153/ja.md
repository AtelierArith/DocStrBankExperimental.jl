```julia
struct ReConstructor{F<:ModelWrappers.FlattenDefault, S<:ModelWrappers.FlattenConstructor, T<:ModelWrappers.UnflattenConstructor}
```

フラット化/非フラット化構造体に関する情報を含みます。

# フィールド

  * `default::ModelWrappers.FlattenDefault`
  * `flatten::ModelWrappers.FlattenConstructor`
  * `unflatten::ModelWrappers.UnflattenConstructor`
