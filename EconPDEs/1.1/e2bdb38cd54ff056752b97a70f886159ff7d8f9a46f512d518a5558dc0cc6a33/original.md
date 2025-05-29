```
pdesolve(f, grid, yend [, τs]; is_algebraic = OrderedDict(k => false for k in keys(yend)), bc = nothing)

solves a system of pdes with an arbitrary number of functions and up to state variable. Denote  F the number of functions to solve for and S the number of state variables.

### Arguments
*  f: is a function (state, y) -> out
where: 
   state is a tuple of real numbers of  length S (for the state values)
   y is a tuple of real numbers of length F * 3 with the functions as well as their first and second derivatives at the state
   out is a named tuple of length F with the value of the time derivatives of the functions at the state 
* grid is an OrderedDict that, for each state, associates an AbstractVector (for the grid)
* yend is an OrderedDict that gives the terminal value of each function in the system of PDEs
* τs (optional) is a time grid on which to solve the pde on. In this case, yend corresponds to the solution at time τs[end]
```
