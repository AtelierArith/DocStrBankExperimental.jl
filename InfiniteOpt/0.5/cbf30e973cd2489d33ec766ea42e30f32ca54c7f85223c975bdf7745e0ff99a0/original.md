```
FiniteDifference{T <: FDTechnique} <: NonGenerativeDerivativeMethod
```

A `DataType` for information about finite difference method applied to  a derivative evaluation. Note that the constructor is of the form:

```julia
    FiniteDifference([technique::FDTechnique = Backward()],
                     [add_boundary_constr::Bool = true])
```

where `technique` is the indicated finite difference method to be applied and  `add_boundary_constr` indicates if the finite difference equation corresponding to  a boundary support should be included. Thus, for backward difference since corresponds to the terminal point and for forward difference this corresponds to  the initial point. We recommend using `add_boundary_constr = false` when an final  condition is given with a backward method or when an initial condition is given  with a forward method. Note that this argument is ignored for central finite  difference which cannot include any boundary points.

**Fields** 

  * `technique::T`: Mathematical technqiue behind finite difference
  * `add_boundary_constraint::Bool`: Indicate if the boundary constraint should be  included in the transcription (e.g., the terminal boundary backward equation for  backward difference)
