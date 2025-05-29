```
 energy(ass::AtomicSubShell)
 energy(elm::Element, ss::SubShell)
```

The edge energy in eV for the specified AtomicSubShell

Example:

```
julia> energy(n"Fe L3")
708.0999999999999
julia> energy(n"Fe", n"L3")
708.0999999999999

energy(elm::Element, tr::Transition)::Float64
energy(cxr::CharXRay)
```

The characteristic X-ray energy for the specified element / transition or characteristic X-ray.
