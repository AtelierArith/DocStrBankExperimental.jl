```
initialize()
```

Generates all the circuit elements for ease of use in building circuits.

It adds the following variables to your environment     r = Resistor()     c = Capacitor()     l = Inductor()     q = CPE()     wo = Warburg("open")     ws = Warburg("short") From here you can quickly build circuits and adjust the parameters directly  using the overloaded * and ^ operators as desired

# Examples

```julia
using EISAnalysis
eval(initialize())
print(r.R)

# output

1.0
```
