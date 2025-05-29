```julia
struct Gain{G, IP, OP, RO, var"356", var"357", var"358", Symbol, var"359"} <: Causal.AbstractStaticSystem
```

Constructs a `Gain` whose output function `g` is of the form 

$$
    y = g(u, t) =  K u
$$

where $K$ is `gain`, $u$ is the value of `input` and `y` is the value of `output`.

# Fields

  * `gain::Any`: Gain
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
julia> K = [1. 2.; 3. 4.];

julia> sfunc = Gain(input=Inport(2), gain=K);

julia> sfunc.readout([1., 2.], 0.) == K * [1., 2.]
true
```
