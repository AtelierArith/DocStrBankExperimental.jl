```
mutable struct PDEDescription
    name::String
    equation_names::Array{String,1}
    unknown_names::Array{String,1}
    variables::Array{Array{String,1},1}
    algebraic_constraint::Array{Bool,1}
    LHS::Array{Array{AbstractPDEOperator,1},2}
    RHS::Array{Array{AbstractPDEOperator,1},1}
    BoundaryOperators::Array{BoundaryOperator,1}
    GlobalConstraints::Array{AbstractGlobalConstraint,1}
end
```

struct that describes a PDE system with n equations and n unknowns

A PDE system is described by

  * its name
  * the names of its equations
  * the names of its unknowns
  * the variables for ansatz and testfunctions of unknowns
  * is the variable related to an algebraic constraint? (e.g. pressure in incompressible CFD, this has implications e.g. for the time discretisation)
  * a size n x n array of Array{AbstractPDEOperator,1} LHS that describes the left-hand sides
  * a length n array of Array{AbstractPDEOperator,1} RHS that describes the right-hand sides
  * a length n array of BoundaryOperators that describes the boundary conditions for each unknown
  * an array of GlobalConstraints that describes additional global constraints

A PDEDescription mainly is a set of PDEOperators arranged in a quadratic n by n matrix (LHS). Every matrix row refers to one equation and the positioning of the PDEOperators (e.g. a bilinearform) immediately sets the information which unknowns have to be used to evaluate the operator. Also  nonlinear PDEOperators are possible where extra information on the further involved uknowns have to be specified. UserData is also assigned to the PDEDescription depending on their type. Operator coefficients are assigned directly to the PDEOperators (in form of AbstractActions or a constant factor), right-hand side data is assigned to the right-hand side array of PDEOperators (RHS) and boundary data is assigned to the BoundaryOperators of the PDEDescription. Additionaly global constraints (like a global zero integral mean) can be assigned as a GlobalConstraint.
