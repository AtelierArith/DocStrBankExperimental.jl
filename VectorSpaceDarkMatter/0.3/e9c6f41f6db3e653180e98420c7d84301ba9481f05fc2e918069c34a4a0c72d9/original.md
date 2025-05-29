```
f_uSph(f::Function; z_even=false, phi_even=false, 
    phi_cyclic=1, phi_symmetric=false, center_Z2=false)
```

Struct that adds decorations to a function $f(u, \theta, \phi)$ that tell `ProjectF` various properties about the function that speed up integration.

`z_even` : (boolean) if `f_uSph(x,y,z)` = `f_uSph(x,y,-z)`. Implies             $\langle \ell m | f \rangle = 0$ if $(\ell+m)$ is odd

`phi_even` : (boolean) if `f_uSph(u,theta,phi)` = `f_uSph(u,theta,-phi)`              Implies $\langle \ell m | f \rangle$ = 0 if $m < 0$

`phi_cyclic` : (integer) if `f_uSph(u,theta,phi)` = `f_uSph(u,theta,phi + 2*pi/n)`

`phi_symmetric` : (boolean) if `f_uSph(u,theta)` is independent of `phi`

`center_Z2` : (boolean) if $f(\vec{u}) = f(-\vec{u})$ is symmetric under                 central inversion. Implies $\langle \ell m | f \rangle = 0$                 if $\ell$ is odd
