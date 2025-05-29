```
Mechanism{T}

Multi-rigid-body system. 

origin: global reference frame represented with Origin
joints: list of JointConstraint objects
bodies: list of Body objects
contacts: list of ContactConstraint objects
system: graph-based representation for mechanism
residual_entries: containt entries for linear system residual
data_matrix: contains parameter information that is fixed during simulation
root_to_leaves: list of node connections traversing from root node to leaves
timestep: time discretization
input_scaling: input scaling for internal use of impulses (default: timestep)
gravity: force vector resulting from gravitational potential
μ: complementarity violation (contact softness)
```
