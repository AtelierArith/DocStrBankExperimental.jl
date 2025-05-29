Source: FMISpec3.0, Version D5ef1c1: 2.3.1. Super State: FMU State Setable

Argument fmuType defines the type of the FMU:

  * fmi3ModelExchange: FMU with initialization and events; between events simulation of continuous systems is performed with external integrators from the environment.
  * fmi3CoSimulation: Black box interface for co-simulation.
  * fmi3ScheduledExecution: Concurrent computation of model partitions on a single computational resource (e.g. CPU-core)
