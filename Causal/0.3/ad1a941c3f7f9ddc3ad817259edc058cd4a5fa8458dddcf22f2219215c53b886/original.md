```julia
struct Adder{S, IP, OP, RO, var"356", var"357", var"358", Symbol, var"359"} <: Causal.AbstractStaticSystem
```

Construts an `Adder` with input bus `input` and signs `signs`. `signs` is a tuplle of `+` and/or `-`. The output function `g` of `Adder` is of the form,

$$
    y = g(u, t) =  \sum_{j = 1}^n s_k u_k
$$

where `n` is the length of the `input`, $s_k$ is the `k`th element of `signs`, $u_k$ is the `k`th value of `input` and $y$ is the value of `output`. The default value of `signs` is all `+`.

# Fields

  * `signs::Any`: Addition signs
  * `input::Any`: Input port
  * `output::Any`: Output port
  * `readout::Any`: Readout function
  * `trigger::Any`
  * `handshake::Any`
  * `callbacks::Any`
  * `name::Any`
  * `id::Any`

# Example

```jldoctest
julia> adder = Adder(signs=(+, +, -));

julia> adder.readout([3, 4, 5], 0.) == 3 + 4 - 5
true
```
