```
phun(str::String; system_of_units = :SI, base_time_units = :SEC)
```

Evaluate an expression in physical units.

Inputs: –`system_of_units`

```
if system_of_units  ==  :US
   basic assumed units are American Engineering:
   LENGTH = FT, TIME = SEC, MASS = SLUG TEMPERATURE = RAN FORCE = LB
elseif system_of_units  ==  :CGS
   basic assumed units are Centimeter,Gram,Second:
   LENGTH = CM, TIME = SEC, MASS = GM TEMPERATURE = K FORCE = DYNE
elseif system_of_units  ==  :IMPERIAL
   basic assumed units are Imperial:
   LENGTH = FT, TIME = SEC, MASS = SLUG TEMPERATURE = RAN FORCE = LB
otherwise,
   basic assumed units are :SIM (equivalent to :SI, default):
   LENGTH = M , TIME = SEC, MASS = KG   TEMPERATURE = K   FORCE = N
```

–`base_time_units` defaults to :SEC

# Example

```
pu = ustring -> phun(ustring; system_of_units = :SIMM)
E1s = 130.0*pu("GPa")
```

yields 1.3e+5 (in mega Pascal) whereas

```
130.0*phun("GPa"; system_of_units = :SI)
```

yields 1.3e+11 (in Pascal)
