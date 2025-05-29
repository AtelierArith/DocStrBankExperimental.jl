```
@op(name, basis=SpinBasis(1//2))
```

`SOperator`型の記号演算子を定義します。デフォルトでは、定義された基底はスピン-1/2基底です。

```jldoctest
julia> @op A
A

julia> @op B FockBasis(2)
B
```
