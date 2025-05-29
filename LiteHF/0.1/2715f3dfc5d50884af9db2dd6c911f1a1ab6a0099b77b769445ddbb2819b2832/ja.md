```
struct ExpCounts{T, M} #Mは展開の目的のための長いタプルです。
    nominal::T
    modifier_names::Vector{Symbol}
    modifiers::M
end
```

修飾子の迷惑パラメータ値が与えられたときに期待されるカウントを返す呼び出し可能な構造体です。渡されるパラメータの数は`modifiers`の長さと等しくなければなりません。詳細は[_expkernel](@ref)を参照してください。
