```
LinDistFlow.add_variables(m::JuMP.AbstractModel, p::Inputs{MultiPhase})
```

define: Pj, Qj, Pij, Qij, vsqrd

TODO:

  * currently indexed bus/edge, phase, time
  * but want to align with BranchFlowMmodel MultiPhase: time, bus/edge, phase (broadest to narrowest)
  * and standardize variable containers in CommonOPF
  * but using nested Dicts makes variable construction slow b/c have to create one at time,   (which was necessary in MultiPhase BranchFlowModel) - but maybe not a big deal
