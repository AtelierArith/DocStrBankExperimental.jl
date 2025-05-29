```julia
struct CoherencyMatrix{B1, B2, T} <: StaticArraysCore.FieldMatrix{2, 2, T}
```

Coherency matrix for a single baseline with bases `B1` and `B2`. The two bases correspond to the type of feeds used for each telescope and should be subtypes of `PolBasis`. To see which bases are implemented type `subtypes(Rimes.PolBasis)` in the REPL.

For a circular basis the layout of the coherency matrix is

```
RR* RL*
LR* RR*
```

which can be constructed using

```julia-repl
c = CoherencyMatrix(RR, LR, RL, LL, CirBasis())
```

For a linear basis the layout of the coherency matrix is

```
XX* XY*
YX* YY*
```

which can be constructed using

```julia-repl
c = CoherencyMatrix(XX, YX, XY, YY, CirBasis())
```

For a mixed (e.g., circular and linear basis) the layout of the coherency matrix is

```
RX* RY*
LX* LY*
```

or e.g., linear and circular the layout of the coherency matrix is

```
XR* XL*
YR* YL*
```

These coherency matrices can be constructed using:

```julia-repl
# Circular and linear feeds i.e., |R><X|
c = CoherencyMatrix(RX, LX, RY, LY, LinBasis(), CirBasis())
# Linear and circular feeds i.e., |X><R|
c = CoherencyMatrix(XR, YR, XL, YL, LinBasis(), CirBasis())
```
