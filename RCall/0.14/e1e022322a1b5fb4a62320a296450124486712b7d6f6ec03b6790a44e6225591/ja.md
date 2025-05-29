```
SxpHead <: Sxp
```

R Sxp ヘッダー (`SEXPREC_HEADER`)。

未知の型に対してこれへのポインタが使用されます。

# フィールド

  * `info::SxpPtrInfo`
  * `attrib::Ptr{Cvoid}`
  * `gc_next::Ptr{Cvoid}`
  * `gc_prev::Ptr{Cvoid}`
