```
NWI(eigen=LinearAlgebra.eigen)
```

NWI (Nocedal Wright Iterative) is a trust region sub-problem solver that sol-   ves the quadratic programming problem subject to the solution being in a   Euclidean ball. It is appropriate for all types of Hessians. It solves the   problem by solving the secular equation by a safeguarded Newton's method.   The secular equation is simply a the inverse of the difference between the   step length and the trust region radius. It accepts either the Newton step   if this is interior and the Hessian is positive definite, or steps to the   boundary (with some slack) in a clever way.The implementation is found in   section 4.3 of [NocedalWrightBook2nd]

NWI accepts all Hessians and is therefore well-suited for Newton's method for   any vexity. It is expensive for very large problems, and uses the direct   eigensolution. This could potentially be useful for problems with simple   structure of the eigenproblem, but I suspect NWI is superior in most cases.

A custom `eigen` solver can be used either by providing a special matrix class   for the Hessian, or by passing in a function to the NWI constructor. This function   must follow the same input/output patterns as LinearAlgebra.eigen.
