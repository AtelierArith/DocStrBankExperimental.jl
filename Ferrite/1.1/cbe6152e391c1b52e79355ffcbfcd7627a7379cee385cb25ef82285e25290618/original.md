```
getnormal(iv::InterfaceValues, qp::Int; here::Bool=true)
```

Return the normal vector in the quadrature point `qp` on the interface. If `here = true` (default) the outward normal to the "here" element is returned, otherwise the outward normal to the "there" element.
