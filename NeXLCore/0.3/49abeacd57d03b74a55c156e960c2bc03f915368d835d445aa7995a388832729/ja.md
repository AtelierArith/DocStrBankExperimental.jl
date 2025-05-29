```
 atomicsubshells(elm::Element, maxE=1.0e6)::Vector{AtomicSubShell}
```

指定された元素に関連するすべてのAtomicSubShell構造体を、指定されたエネルギー（eV単位）未満で含むVectorを返します。

例:

```
julia> atomicsubshells(n"Fe",1.0e3)
8-element Array{AtomicSubShell,1}:
 Fe M3
 Fe L3
 Fe M5
 Fe L1
 Fe L2
 Fe M1
 Fe M4
 Fe M2
```
