Abstract base class for all operators.

All deriving operator classes have to define the fields `basis_l` and `basis_r` defining the left and right side bases.

For fast time evolution also at least the function `mul!(result::Ket,op::AbstractOperator,x::Ket,alpha,beta)` should be implemented. Many other generic multiplication functions can be defined in terms of this function and are provided automatically.
