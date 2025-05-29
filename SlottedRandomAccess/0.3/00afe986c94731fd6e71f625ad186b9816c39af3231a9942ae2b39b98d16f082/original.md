```julia
struct CRDSA{N} <: SlottedRandomAccess.FixedRepSlottedRAScheme{N}
```

Type representing the *Contention Resolution Diversity Slotted ALOHA* (CRDSA) scheme, with a number of replicas `N`.

This RA scheme was introduced in [this 2007 IEEE paper](https://doi.org/10.1109/TWC.2007.348337).

See also: [`MF_CRDSA`](@ref)
