```
RheoModelClass(;name::String, p::Tuple, G,J,Gp,Gpp, constraint, info, G_ramp)
```

`RheoModelClass` is a complex data structure that contains all the relevant data to  allow RHEOS to fit models and make predictions once parameters are set. RHEOS possesses already a large number of such data structures to represent common rheological models, such as Maxwell or KelvinVoigt.

Users are not expected to directly manipulate the content of a RheoModelClass object, but will  pass it to relevant functions for fitting and numerically evaluating visco-elastic moduli.

The model name and its parameters can however be printed and display on the REPL.

# Example

```@example
julia> Maxwell

Model name: maxwell

Free parameters: η and k

                ___
            _____| |________╱╲  ╱╲  ╱╲  ___
                _|_|          ╲╱  ╲╱  ╲╱
                  η                  k
               
```
