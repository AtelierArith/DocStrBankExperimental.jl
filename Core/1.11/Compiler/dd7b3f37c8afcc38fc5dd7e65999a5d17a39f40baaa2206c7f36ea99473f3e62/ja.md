```
cnd::Conditional
```

この値の型は `Bool` である可能性があります。しかし、限られた量の逆伝播を可能にするために、この `Bool` 値がどのように作成されたかに関する情報も保持します。特に、この値で分岐する場合、真の分岐では `SlotNumber(cnd.slot)` の型が `cnd.thentype` によって制限され、偽の分岐では `cnd.elsetype` によって制限されると仮定できます。例：

```julia
let cond = isa(x::Union{Int, Float}, Int)::Conditional(x, Int, Float)
    if cond
       # ここで x は `Int` であると仮定できます
    else
       # ここで x は `Float` であると仮定できます
    end
end
```
