```
residuals(ARX::TransferFunction, d::InputOutputData)
```

Calculates the residuals `v = Ay - Bu` of an ARX process and InputOutputData d. The length of the returned residuals is `length(d) - max(na, nb)`

# Example:

```jldoctest
julia> ARX = tf(1, [1, -1], 1)
TransferFunction{Discrete{Int64}, ControlSystemsBase.SisoRational{Int64}}
  1
-----
z - 1

Sample Time: 1 (seconds)
Discrete-time transfer function model

julia> u = 1:5
1:5

julia> y = lsim(ARX, u, 1:5)[1][:]
5-element Vector{Float64}:
  0.0
  1.0
  3.0
  6.0
 10.0

julia> d = iddata(y, u)
InputOutput data of length 5 with 1 outputs and 1 inputs

julia> residuals(ARX, d)
4-element Vector{Float64}:
 0.0
 0.0
 0.0
 0.0
```
