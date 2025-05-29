```
HamiltonJacobiEvolution(stencil::Stencil,model,space,tol,max_steps,max_steps_reinit)
```

Create an instance of `HamiltonJacobiEvolution` given a stencil, model, FE space, and  additional optional arguments. This automatically creates the DoF permutation to handle high-order finite elements. 
