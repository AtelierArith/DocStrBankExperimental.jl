```
pqn(objective, x, projection, options; ls=nothing, callback=nothing)
```

Function for using a limited-memory projected quasi-Newton to solve problems of the form   min objective(x) s.t. x in C

The projected quasi-Newton sub-problems are solved the spectral projected gradient algorithm

# Arguments

  * `funObj(x)`: function to minimize (returns gradient as second argument)
  * `funProj(x)`: function that returns projection of x onto C
  * `x`: Initial guess
  * `options`: pqn_options structure

# Optional Arguments

  * `ls` `: User provided linesearch function
  * `callback` : Callback function. Must take as input a `result` callback(x::result)

# Notes:

```
Adapted fromt he matlab implementation of minConf_PQN
```
