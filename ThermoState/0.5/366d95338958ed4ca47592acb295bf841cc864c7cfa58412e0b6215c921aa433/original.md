```
amount_type(st::ThermodynamicState)
```

given a state, returns a tuple with information about how is the amount of matter specified.

The first element of the tuple is related to the number of components present in the state. if it has only one component. it will return `SingleComponent`. if a multicomponent specification (`MaterialCompounds`) is defined, it will return that type instead.

The second element is related to the type of material specified (molar or mass). if there isn't any specification, it will assume one mol, via the type `OneMol`. It will return a `MaterialAmount`   if it is specified.

## Examples

```julia-repl
julia> tp = state(t=1,p=2)
ThermodynamicState with 2 properties:
  Temperature : 1[K]
  Pressure : 2[Pa]

julia> amount_type(tp)
(SingleComponent(), OneMol())

julia> tpn = state(t=1,p=2,mass=3)
ThermodynamicState with 3 properties:
  Temperature : 1[K]
  Pressure : 2[Pa]
  Mass : 3[kg]

julia> amount_type(tpn)
(SingleComponent(), MaterialAmount{MASS}())

julia> tpxm = state(t=1,p=2,mass=3,xn = [0.1,0.9])      
ThermodynamicState with 4 properties:
  Temperature : 1[K]
  Pressure : 2[Pa]
  Mass : 3[kg]
  Molar fraction : [0.1, 0.9]

julia> amount_type(tpxm)
(MaterialCompounds{MOLAR, FRACTION}(), MaterialAmount{MASS}())

julia> tpm = state(t=1,p=2,m = [1,2])
ThermodynamicState with 3 properties:
  Temperature : 1[K]
  Pressure : 2[Pa]
  Mass amounts : [1, 2][kg]

julia> amount_type(tpm)
(MaterialCompounds{MASS, TOTAL_AMOUNT}(), MaterialCompounds{MASS, TOTAL_AMOUNT}())
```
