```
state(;normalize_units=true,check=true,kwargs...)
state(args...;check=true)
state((specs...))
```

Creates a `ThermodynamicState` from the arguments passed. If one or more of the arguments is the value `VariableSpec()`, the state created will be a callable,  returning a complete state when evaluated.

`Unitful` quantities are normalized to SI units and unit-stripped.  This can be disabled with `normalize_units=false`

When creating a thermodynamic state, the input arguments are checked for consistency with the gibbs rule. This check can be skipped with `check=false`

if called with a tuple of specs, all the checks are skipped, allowing defining states at compile time. this form does not allow variable specifications.

## examples:

```
st1 = state(t=1,p=2,mass=3) #keyword interface

t0 = spec(spec"t",1)
p0 = spec(spec"p",2)
mass0 = spec(spec"mass",3)
st2 = state(t0,p0,mass0) # positional arguments interface

st3 = state((t0,p0,mass0)) #no runtime cost, not checked

st4 = state(t=1,T=2,p=3,P=4) #errors, spends a determinate amount of time checking for errors
st4 = state(t=1,T=2,p=3,P=4,check=false) #doesnt error, doenst check


```
