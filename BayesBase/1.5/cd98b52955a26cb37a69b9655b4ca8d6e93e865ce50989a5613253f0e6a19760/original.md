```
LinearizedProductOf
```

An efficient **linearized** implementation of product of multiple distributions. This structure prevents `ProductOf` tree from growing too much in case of identical objects.  This trick significantly reduces Julia compilation times when closed product rules are not available but distributions are of the same type. Essentially this structure linearizes leaves of the `ProductOf` tree in case if it sees objects of the same type (via dispatch).

See also: [`ProductOf`](@ref), [`GenericProd`]
