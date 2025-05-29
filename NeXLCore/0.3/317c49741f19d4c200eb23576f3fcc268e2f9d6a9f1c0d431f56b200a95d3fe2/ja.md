```
 energy(ass::AtomicSubShell)
 energy(elm::Element, ss::SubShell)
```

指定されたAtomicSubShellのエッジエネルギー（eV）

例：

```
julia> energy(n"Fe L3")
708.0999999999999
julia> energy(n"Fe", n"L3")
708.0999999999999

energy(elm::Element, tr::Transition)::Float64
energy(cxr::CharXRay)
```

指定された元素/遷移または特性X線の特性X線エネルギー。
