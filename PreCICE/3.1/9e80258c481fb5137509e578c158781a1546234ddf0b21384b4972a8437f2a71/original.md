```
createParticipant(participantName::String, configFilename::String, solverProcessIndex::Integer, solverProcessSize::Integer)
```

Create the coupling interface and configure it. Must get called before any other method of this interface.

# Arguments

  * `participantName::String`: Name of the participant from the xml configuration that is using the interface.
  * `configFilename::String`: Name (with path) of the xml configuration file.
  * `solverProcessIndex::Integer`: If the solver code runs with several processes, each process using preCICE has to specify its index, which has to start from 0 and end with solverProcessSize - 1.
  * `solverProcessSize::Integer`: The number of solver processes of this participant using preCICE.

# Examples

```julia
createParticipant("SolverOne", "./precice-config.xml", 0, 1)
```
