```
Derivative{F <: Function, V <: GeneralVariableRef} <: JuMP.AbstractVariable
```

A `DataType` for storing core infinite derivative information. This follows a  derivative of the form: $\frac{\partial x(\alpha, \hdots)}{\partial \alpha}$  where $x(\alpha, \hdots)$ is an infinite variable and $\alpha$ is an infinite  parameter. Here, both $x$ and $\alpha$ must be scalars. 

It is important to note that `info.start` should contain a start value function that generates the start value for a given infinite parameter support. This function should map a support to a start value using user-formatting if `is_vector_start = false`, otherwise it should do the mapping using a single support vector as input. Also, the variable reference type `V` must pertain to infinite variables and parameters.

**Fields**

  * `info::JuMP.VariableInfo{Float64, Float64, Float64, F}`: JuMP variable information.
  * `is_vector_start::Bool`: Does the start function take support values formatted as vectors?
  * `variable_ref::V`: The variable reference of the infinite variable argument.
  * `parameter_ref::V`: The variable reference of the infinite parameter the defines the  differential operator.
