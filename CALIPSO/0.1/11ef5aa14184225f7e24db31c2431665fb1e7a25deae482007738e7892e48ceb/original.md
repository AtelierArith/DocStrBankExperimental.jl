```
Dynamics(dynamics, num_next_state, num_state, num_action;
    num_parameter, checkbounds, constraint_tensor)

dynamics type 

dynamics: Function 
num_next_state: Int - dimension of next state
num_state: Int - dimension of current state 
num_action: Int - dimension of current action 
num_parameter: Int - dimension of problem data 
checkbounds: Bool - flag for checking @inbounds for codegen methods 
constraint_tensor: Bool - flag for generating second-derivative methods
```
