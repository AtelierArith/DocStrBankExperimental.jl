```
Solver(methods, num_variables, num_parameters, num_equality, num_cone;
    parameters, nonnegative_indices, second_order_indices, custom, options)

CALIPSO solver 

methods: ProblemMethods - includes objective and constraint functions, as we as their derivatives 
num_variables: Int - dimension of primal decision variables 
num_parameters: Int - dimension of problem data 
num_equality: Int - dimension of equality constraints 
num_cone: Int - dimension of cone constraints 
parameters: Vector{Real} - problem data 
nonnegative_indices: Vector{Int} - indices of cone constraints corresponding to nonnegative orthant 
second_order_indices: Vector{Vector{Int}} - indices of cone constraints corresponding to second-order cones
custom: Any - user-provided type used for solver callbacks 
options: Options - solver settings
```
