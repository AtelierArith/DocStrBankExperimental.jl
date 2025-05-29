```
ODEFunctionList
```

## Constructor

`ODEFunctionList(state=nothing,constraint=nothing,ode_rhs=nothing,bc_rhs=nothing,constraint_force=nothing,bc_op=nothing,lin_op=nothing)`

Supply functions and data types for a constrained ODE system. The specified functions must provide the various parts that comprise the constrained ODE system

$\dfrac{dy}{dt} = Ly - B_1 z + r_1(y,t)$

$B_2 y + C z = r_2(t)$

The functions can be in in-place or out-of-place form, but they must all be consistently of the same form.

  * `state =` specifies a prototype of the state vector $y$.
  * `constraint =` specifies a prototype of the constraint force vector $z$. If there are no constraints, this can be omitted.
  * `ode_rhs =` specifies the right-hand side of the ODEs, $r_1$. The in-place form of the function is `r1(dy,y,x,sys::ILMSystem,t)`, the state vector `y`, IL system `sys`, time `t`, and returning $dy/dt$. The out-of-place form is `r1(y,x,sys,t)`.
  * `bc_rhs =` specifies the right-hand side of the boundary conditions, $r_2$. If there are no constraints, this can be omitted. The in-place form is `r2(dz,x,sys,t)`, returning `dz`, the part of the boundary constraint not dependent on the state vector. The out-of-place form is `r2(x,sys,t)`.
  * `constraint_force =` supplies the constraint force term in the ODEs, $B_1 z$. If there are no constraints, this can be omitted. The in-place form is `B1(dy,z,x,sys)`, returning the contribution to $dy/dt$ (with the sign convention shown in the equations above) and the out-of-place form is `B1(z,x,sys)`.
  * `bc_op =` supplies the left-hand side of the boundary constraint, $B_2 y$. If there are no constraints, this can be omitted. The in-place form is `B2(dz,y,x,sys)`, the out-of-place form is `B2(y,x,sys)`.
  * `bc_regulator =` supplies the boundary constraint's regulation operation, $C z$. If there is none, this can be omitted. The in-place form is `C(dz,z,x,sys)`, the out-of-place form is `C(z,x,sys)`.
  * `ode_implicit_rhs =` specifies an optional part of the RHS to be treated implicitly. If there is none, this can be omitted. The in-place form is `r1imp(dy,x,sys,t)`, the out-of-place form is `r1imp(x,sys,t)`.
  * `lin_op =` is optional and specifies a linear operator on the state vector $L$, to be treated with an exponential integral (i.e., integrating factor) in the time marching. (Alternatively, this part can simply be included in `r_1`). It should have an associated `mul!` operation that acts upon the state vector.
