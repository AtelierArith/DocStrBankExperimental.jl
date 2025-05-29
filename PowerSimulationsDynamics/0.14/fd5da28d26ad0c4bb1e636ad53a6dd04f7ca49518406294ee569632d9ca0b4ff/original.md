```
function NetworkSwitch(
    time::Float64,
    ybus::SparseArrays.SparseMatrixCSC{Complex{Float64}, Int},
)
```

Allows to modify directly the admittance matrix, Ybus, used in the Simulation. This allows the user to perform branch modifications, three phase faults (with impedance larger than zero) or branch trips, as long as the new Ybus provided captures that perturbation.

# Arguments:

  * `time::Float64` : Defines when the Network Switch will happen. This time should be inside the time span considered in the Simulation
  * `ybus::SparseArrays.SparseMatrixCSC{Complex{Float64}, Int}` : Complex admittance matrix
