```
number_field(f::Vector{QQPolyRingElem}, s::VarName="_\$") -> AbsNonSimpleNumField
```

$ f = (f*1, \ldots, f*n) $ を一変数有理多項式とすると、$ K = Q[t*1, \ldots, t*n]/\langle f*1(t*1), \ldots, f*n(t*n)\rangle $ を構成します。このイデアルは最大でなければなりませんが、これはテストされません。
