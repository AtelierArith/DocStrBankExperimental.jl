```
PoleLadderTransport <: AbstractVectorTransportMethod
```

Specify to use [`pole_ladder`](@ref) as vector transport method within [`vector_transport_to`](@ref) or [`vector_transport_direction`](@ref), i.e.

Let $X∈ T_p\mathcal M$ be a tangent vector at $p∈\mathcal M$ and $q∈\mathcal M$ the point to transport to. Then $x = \exp_pX$ is used to call `y =`[`pole_ladder`](@ref)`(M, p, x, q)` and the resulting vector is obtained by computing $Y = -\log_qy$.

The [`PoleLadderTransport`](@ref) posesses two advantages compared to [`SchildsLadderTransport`](@ref):

  * it is cheaper to evaluate, if you want to transport several vectors, since the mid point $c$ then stays unchanged.
  * while both methods are exact if the curvature is zero, pole ladder is even exact in symmetric Riemannian manifolds [Pennec:2018](@cite)

The pole ladder was was proposed in [LorenziPennec:2013](@cite). Its name stems from the fact that it resembles a pole ladder when applied to a sequence of points usccessively.

# Constructor

```julia
PoleLadderTransport(
    retraction = ExponentialRetraction(),
    inverse_retraction = LogarithmicInverseRetraction(),
)
```

Construct the classical pole ladder that employs exp and log, i.e. as proposed in[LorenziPennec:2013](@cite). For an even cheaper transport the inner operations can be changed to an [`AbstractRetractionMethod`](@ref) `retraction` and an [`AbstractInverseRetractionMethod`](@ref) `inverse_retraction`, respectively.
