```
push!(ir, x)
```

IRまたはブロック`ir`にステートメントまたは式`x`を追加し、新しい変数を返します。 [`pushfirst!`](@ref)や[`insert!`](@ref)も参照してください。

```
julia> ir = IR();

julia> x = argument!(ir)
%1

julia> push!(ir, xcall(:*, x, x))
%2

julia> ir
1: (%1)
  %2 = %1 * %1
```
