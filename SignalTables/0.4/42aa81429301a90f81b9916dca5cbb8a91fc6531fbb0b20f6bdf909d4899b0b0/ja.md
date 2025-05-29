```
getSignalInfo(signalTable, name::String)
```

信号を返しますが、[`Var`](@ref) または [`Par`](@ref) は :values または :value ではなく、代わりに :*eltypeOrType (値が AbstractArray の場合はその eltype、そうでない場合は値の typeof) と :*size (値に定義されている場合) を持ちます。

`name` が存在しない場合、エラーが発生します。

この関数は、信号の属性のみが必要で、値は必要ない場合に便利です（属性を返すことは *安価* な操作である可能性がありますが、値を返すことは *高価* な操作である可能性があります）。
