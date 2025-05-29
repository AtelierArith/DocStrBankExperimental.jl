```julia
struct SolidMechanics{NF, NP, NS, Mat, Form, P<:Cthonios.StressDivergence{NF, NP, NS, Mat, Form}} <: Cthonios.AbstractPhysics{NF, NP, NS}
```

  * `material_model::Any`
  * `formulation::Any`
  * `stress_divergence::Cthonios.StressDivergence{NF, NP, NS, Mat, Form} where {NF, NP, NS, Mat, Form}`
