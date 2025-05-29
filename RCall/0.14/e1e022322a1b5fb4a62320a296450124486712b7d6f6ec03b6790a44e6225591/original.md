```
SxpHead <: Sxp
```

R Sxp header (`SEXPREC_HEADER`).

A pointer to this is used for unknown types.

# Fields

  * `info::SxpPtrInfo`
  * `attrib::Ptr{Cvoid}`
  * `gc_next::Ptr{Cvoid}`
  * `gc_prev::Ptr{Cvoid}`
