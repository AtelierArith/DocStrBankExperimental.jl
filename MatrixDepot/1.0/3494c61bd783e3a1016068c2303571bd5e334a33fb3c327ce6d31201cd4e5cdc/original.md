julia     MatrixDepot

Give access to a wealth of sample and test matrices and accompanying data. A set of matrices is generated locally (with arguments controlling the special case). Another set is loaded from one of the publicly accessible matrix collections `SuiteSparse Matrix Collection` (formerly `University of Florida Matrix Collection`) and the `Matrix Market Collection`.

Access is like

```
using MatrixDepot

A = matrixdepot("hilb", 10) # locally generated hilbert matrix dimensions (10,10)

A = matrixdepot("HB/1138_bus")     # named matrix of the SuiteSparse Collection
A = matrixdepot(sp(1))             # same matrix using numerical id
A = matrixdepot("Harwell*/*/1138_bus") # matrix from the Matrix Market Collection

md = mdopen("*/bfly")   # named matrix with some extra data
A = md.A
co = md.coord
tx = md("Gname_10.txt")

md = mdopen("gravity", 10, false) # locally generated example with rhs and solution
A = md.A
b = md.b
x = md.x
```

###### commands:

```
mdinfo, listdir, listgroups, matrixdepot, mdopen, listdata, mdlist,
metasymbols, setgroup!, deletegroup!.
```

###### selector patterns:

```
strings, string-patterns (using "*", "?", "[]", "/", "**"), regular expressions: for names
builtin(42), user(3,5), sp(10:11,6,2833), mm(1), mm(:): to access by integer id or all
sp(pattern), mm(pattern) to access corresponding (alternative) matrix for other collection
```

###### predicate patterns:

```
isboolean, isinteger, isreal, iscomplex
isgeneral, issymmetric, ishermitian, isskew
isbuiltin, isuser, islocal, isremote, isloaded, isunloaded
issvdok
keyword(string expression), logical, hasdata(symbol), @pred(expression)

see also: "logical" for logical combinations of all kinds of patterns.
```
