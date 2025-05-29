```
POMDPFile
```

Writes a pomdpx file from a pomdp defined using the explicit interface of POMDPs.jl

# Constructors

  * `POMDPFile(filename)` just stores the file name if the file exists
  * `POMDPFile(pomdp::POMDP, filename="model.pomdpx"; verbose=true)` writes a .pomdpx file from the pomdp definition
