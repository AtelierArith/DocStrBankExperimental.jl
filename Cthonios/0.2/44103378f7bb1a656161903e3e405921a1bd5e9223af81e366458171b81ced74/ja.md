```julia
struct SolidDynamics{NF, NP, NS, Mat, Form, P1<:Cthonios.StressDivergence{NF, NP, NS, Mat, Form}, P2<:Cthonios.Dynamics{NF}} <: Cthonios.AbstractPhysics{NF, NP, NS}
```

  * `material_model::Any`
  * `formulation::Any`
  * `stress_divergence::Cthonios.StressDivergence{NF, NP, NS, Mat, Form} where {NF, NP, NS, Mat, Form}`
  * `dynamics::Cthonios.Dynamics`
