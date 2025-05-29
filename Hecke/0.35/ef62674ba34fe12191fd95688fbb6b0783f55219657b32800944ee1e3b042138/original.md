```
theta(z::Vector{AcbFieldElem},  tau::AcbMatrix}; char::Vector{Vector{Int}},
dz::Vector{Vector{Int}}, dtau::Vector{Vector{Int}}, prec::Int) -> AcbFieldElem
```

Compute the value of the theta(tau, z) with characteristic char with precision the minimum of prec, the precision of z and the precision of tau. Optionally one can set dz to be a list of elements of a standard basis to compute the derivative of the Theta function with characteristic char at the point z in the specified directions. (E.g. in genus 3 setting  dz = [[1,0,0], [0,0,1]] would compute dtheta(z, tau)/(dx1 dx3). Similarly, one can set dtau to be a list of integers tuples to take the derivative with respect to the period matrix tau. (E.g. dtau = [[1,2]] would compute dtheta(z, tau)/dtau_{1,3})
