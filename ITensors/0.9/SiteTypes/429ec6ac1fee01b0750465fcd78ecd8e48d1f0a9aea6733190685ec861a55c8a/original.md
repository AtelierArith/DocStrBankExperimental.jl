```
val(s::Index, name::String)
```

Return an integer corresponding to the `name` of a certain value the Index `s` can take. In other words, the `val` function maps strings to specific integer values within the range `1:dim(s)`.

The `val` function is implemented for various Index tags by overloading methods named `val` which take a `SiteType` argument corresponding to one of the tags of the Index `s` and an `ValName"name"` argument that corresponds to the input name.

# Example

```julia
s = Index(2, "Site,S=1/2")
val(s,"Up") == 1
val(s,"Dn") == 2

s = Index(2, "Site,Fermion")
val(s,"Emp") == 1
val(s,"Occ") == 2
```
