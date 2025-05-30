```
@bra(name, basis=SpinBasis(1//2))
```

シンボリックなブラを `SBra` 型で定義します。デフォルトでは、定義された基底はスピン-1/2基底です。

```jldoctest
julia> @bra b₁
⟨b₁|

julia> @bra b₂ FockBasis(2)
⟨b₂|
```
