```
export_variants(T)
```

すべてのバリアント型を、関数が呼び出されたモジュールにエクスポートします。

## 例

```julia
julia> @sum_structs AB begin
           struct A x::Int end
           struct B y::Int end
       end

julia> AB'.A(1)
AB'.A(1)

julia> export_variants(AB)

julia> A(1) # これも今は動作します
AB'.A(1)
```
