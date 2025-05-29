```julia
struct Coupler{C1, C2, IP, OP, RO, var"356", var"357", var"358", Symbol, var"359"} <: Causal.AbstractStaticSystem
```

Constructs a coupler from connection matrix `conmat` of size $n \times n$ and coupling matrix `cplmat` of size $d \times d$. The output function `g` of `Coupler` is of the form 

$$
    y = g(u, t) = (E \otimes P) u
$$

where $\otimes$ is the Kronecker product, $E$ is `conmat` and $P$ is `cplmat`, $u$ is the value of `input` and `y` is the value of `output`.

# Fields

  * `conmat::Any`: Outer coupling matrix
  * `cplmat::Any`: Inner coupling matrix
  * `input::Any`: Input port
  * `output::Any`: Output port
  * `readout::Any`: Readout function
  * `trigger::Any`
  * `handshake::Any`
  * `callbacks::Any`
  * `name::Any`
  * `id::Any`
