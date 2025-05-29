```
 atomicsubshells(elm::Element, maxE=1.0e6)::Vector{AtomicSubShell}
```

Returns a Vector containing all AtomicSubShell structs associated with the  specified element with less than the specified energy (in eV).

Example:

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
