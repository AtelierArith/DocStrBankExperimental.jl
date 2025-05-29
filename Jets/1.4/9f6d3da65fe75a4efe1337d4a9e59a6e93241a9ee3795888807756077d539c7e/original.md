```
space(R, iblock)
```

Return the `Jets` sub-space associated with block `iblock` in the `Jets` block space `R::JetBSpace`.

# Example

Consider a block operator with 2 row-blocks and 3 column-blocks.  We can use `space` to determine the sub-space associated with the first block of its domain:

```
using Pkg
pkg"add Jets JetPack"
using Jets, JetPack
A = @blockop [JopDiagonal(rand(10)) for irow=1:2, icol=1:3]
space(domain(A), 1) # JetSpace(Float64,10)
```
