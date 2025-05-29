```
operator_parameter(dref::DerivativeRef)::GeneralVariableRef
```

Returns the infinite parameter reference that is what the differential operator  is operating with respect to (i.e., the independent  variable of the derivative).

**Example**

```julia-repl
julia> operator_parameter(dref) 
t
```
