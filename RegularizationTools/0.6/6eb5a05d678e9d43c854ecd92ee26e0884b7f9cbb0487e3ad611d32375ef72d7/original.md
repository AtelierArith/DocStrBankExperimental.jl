```
designmatrix(s::Any, q::Any, f::Function)::AbstractMatrix
```

  * s is an array of setpoints
  * q is an array of query points
  * f is a function that maps the functor [Domain](@ref) to a solution y

The function to creates an array of domain nodes using the standard basis eᵢ of  the vector space. The setpoint or query point can be any abstract notion of the  input. For examples, a numerical value corresponding to a setting, a string label  (["bin A", "bin B", ...), or a list of pixel coordinate [(1,1), (1,2), ...].  The function f must accept a single argument of type [Domain](@ref) and provide a  numerical mapping between input $x$ and output $y$ at query point $q$. The function designmatrix then returns a design matrix $\mathbf{A}$ such that 

$y = \mathbf{A}x$

where x is an array of numerical input values. In the case that [q] = [s], the  shortcut `designmatrix(s, f)` can be used.
