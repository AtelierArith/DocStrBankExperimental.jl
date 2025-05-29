```
@ket(name, basis=SpinBasis(1//2))
```

`SKet`型の記号的なケトを定義します。デフォルトでは、定義された基底はスピン-1/2基底です。

```jldoctest
julia> @ket k₁
|k₁⟩

julia> @ket k₂ FockBasis(2)
|k₂⟩
```
