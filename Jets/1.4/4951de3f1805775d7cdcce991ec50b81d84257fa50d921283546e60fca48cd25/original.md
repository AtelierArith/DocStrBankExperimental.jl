```
@blockop(ex, kwargs)
```

Construct a `Jets` block operator, a combination of Jet operators analogous to a block matrix.

# Examples

example with 1 row-block and 3 column-blocks:

```julia
using Pkg
pkg"add Jets JetPack"
using Jets, JetPack
A = @blockop [JopDiagonal(rand(10)) for icol=1:3]
```

example with 2 row-blocks and 3 column-blocks.

```
using Pkg
pkg"add Jets JetPack"
using Jets, JetPack
A = @blockop [JopDiagonal(rand(10)) for irow=1:2, icol=1:3]
```
