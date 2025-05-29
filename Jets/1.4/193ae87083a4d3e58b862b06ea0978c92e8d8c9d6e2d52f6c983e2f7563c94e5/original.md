```
indices(R, iblock)
```

Return the linear indices associated with block `iblock` in the `Jets` block space `R::JetBSpace`.

# Example

Consider a block operator with 2 row-blocks and 3 column-blocks.  We can use `indices` to determine the elements of the vector that are associatd with the first block of its domain:

```
using Pkg
pkg"add Jets JetPack"
using Jets, JetPack
A = @blockop [JopDiagonal(rand(10)) for irow=1:2, icol=1:3]
indices(domain(A), 1) # returns indices 1:10
```
