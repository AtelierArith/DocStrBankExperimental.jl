```
Constraint(constraint, num_state, num_action;
    num_parameter, checkbounds, constraint_tensor)

constraint type 

constraint: Function 
num_state: Int - dimension of state 
num_action: Int - dimension of action 
num_parameter: Int - dimension of problem data 
checkbounds: Bool - flag for checking @inbounds for codegen methods 
constraint_tensor: Bool - flag for generating second-derivative methods
```
