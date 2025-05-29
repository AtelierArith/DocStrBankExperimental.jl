```
sumblock(ex::String; Ts = 0, n = 1)
```

Create a summation node (named statespace system) that sums (or subtracts) vectors of length `n`.

# Arguments:

  * `Ts`: Sample time
  * `n`: The length of the input and output vectors. Set `n=1` for scalars.

When using `sumblock` to form block diagrams, note how the system returned from `sumblock` has input names corresponding to the right-hand side of the expression and output names corresponding to the variable on the left-hand side. You will thus typically list connections like `:y => :y` in the connection list to the [`connect`](@ref) function. See the tutorials

  * https://juliacontrol.github.io/RobustAndOptimalControl.jl/dev/hinf_connection/
  * https://juliacontrol.github.io/RobustAndOptimalControl.jl/dev/api/#RobustAndOptimalControl.connect-Tuple{Any}

for example usage

# Examples:

```
julia> sumblock("uP = vf + yL")
NamedStateSpace{Continuous, Int64}
D = 
 1  1

With state  names: 
     input  names: vf yL
     output names: uP


julia> sumblock("x_diff = xr - xh"; n=3)
NamedStateSpace{Continuous, Int64}
D = 
 1  0  0  -1   0   0
 0  1  0   0  -1   0
 0  0  1   0   0  -1

With state  names: 
     input  names: xr1 xr2 xr3 xh1 xh2 xh3
     output names: x_diff1 x_diff2 x_diff3
     

julia> sumblock("a = b + c - d")
NamedStateSpace{Continuous, Int64}
D = 
 1  1  -1

With state  names: 
     input  names: b c d
     output names: a
```
