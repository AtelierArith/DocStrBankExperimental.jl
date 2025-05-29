```
function_gradient_jump(iv::InterfaceValues, q_point::Int, u)
function_gradient_jump(iv::InterfaceValues, q_point::Int, u, dof_range_here, dof_range_there)
```

Compute the jump of the function gradient at the quadrature point over the interface along the default normal direction.

This function uses the definition $\llbracket \vec{v} \rrbracket=\vec{v}^\text{there} -\vec{v}^\text{here}$. To obtain the form, $\llbracket \vec{v} \rrbracket=\vec{v}^\text{there} ⋅ \vec{n}^\text{there} + \vec{v}^\text{here} ⋅ \vec{n}^\text{here}$, multiply by minus the outward facing normal to the first element's side of the interface (which is the default normal for [`getnormal`](@ref) with [`InterfaceValues`](@ref)).
