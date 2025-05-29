```
primitivize(siteg::SiteGroup{D}) where D
```

Transform the operations, cosets, and Wyckoff position associated with `siteg` to a primitive setting. 

If the input site group is associated with an trivially centered space group (i.e., centering `'P'` or `'p'`), a direct reference to the input is returned; if not, a new site group is built and returned, sharing no memory with the input.

The transformation of operations and cosets is performed *without* reduction of translations (i.e., passing `modw = false` to [`primitivize(::SymOperation)`](@ref)), consistent with Crystalline's convention of not reducing translations Wyckoff positions. The number of coset operations returned will be pruned, however, if this count is not equal to the number of positions in the primitive-cell orbit. Note that this is different from the behavior of e.g., `primitivize(::LittleGroup)`.
