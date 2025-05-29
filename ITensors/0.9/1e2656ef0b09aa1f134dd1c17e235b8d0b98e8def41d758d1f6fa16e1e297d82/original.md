```
eachindval(is::Index...)
eachindval(is::Tuple{Vararg{Index}})
```

Create an iterator whose values are Index=>value pairs corresponding to a Cartesian indexing over the dimensions of the provided `Index` objects.

# Example

```julia
i = Index(3; tags="i")
j = Index(2; tags="j")
T = random_itensor(j, i)
for iv in eachindval(i, j)
  @show T[iv...]
end
```
