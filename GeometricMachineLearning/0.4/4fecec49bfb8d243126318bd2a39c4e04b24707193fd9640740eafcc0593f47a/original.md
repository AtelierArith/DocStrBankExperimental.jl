```
TransformerIntegrator <: Architecture
```

Encompasses various transformer architectures, such as the [`VolumePreservingTransformer`](@ref) and the [`LinearSymplecticTransformer`](@ref). 

The central idea behind this is to construct an explicit multi-step integrator:

$$
    \mathtt{Integrator}: [ z^{(t - \mathtt{sl} + 1)}, z^{(t - \mathtt{sl} + 2)}, \ldots, z^{(t)} ] \mapsto [ z^{(t + 1)}, z^{(t + 2)}, \ldots, z^{(t + \mathtt{pw})} ],
$$

where `sl` stands for *sequence length* and `pw` stands for *prediction window*, so the numbers of input and output vectors respectively.
