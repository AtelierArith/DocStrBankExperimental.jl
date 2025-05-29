```
shape_gradient_jump(iv::InterfaceValues, qp::Int, i::Int)
```

Compute the jump of the gradient of shape function `i` at quadrature point `qp` across the interface in the default normal direction.

This function uses the definition $\llbracket \vec{v} \rrbracket=\vec{v}^\text{there} -\vec{v}^\text{here}$. To obtain the form, $\llbracket \vec{v} \rrbracket=\vec{v}^\text{there} ⋅ \vec{n}^\text{there} + \vec{v}^\text{here} ⋅ \vec{n}^\text{here}$, multiply by minus the outward facing normal to the first element's side of the interface (which is the default normal for [`getnormal`](@ref) with [`InterfaceValues`](@ref)).
