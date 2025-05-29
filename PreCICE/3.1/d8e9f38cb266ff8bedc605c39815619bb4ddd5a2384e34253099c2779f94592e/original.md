```
createParticipantWithCommunicator(participantName::String, configFilename::String, solverProcessIndex::Integer, solverProcessSize::Integer, communicator::Union{Ptr{Cvoid}, Ref{Cvoid}, Ptr{Nothing}})
```

TODO: Documentation or [WIP] tag. The data types of the communicator are not yet verified.

# See also:

[`createParticipant`](@ref)

# Arguments

  * `participantName::String`: Name of the participant from the xml configuration that is using the interface.
  * `configFilename::String`: Name (with path) of the xml configuration file.
  * `solverProcessIndex::Integer`: If the solver code runs with several processes, each process using preCICE has to specify its index, which has to start from 0 and end with solverProcessSize - 1.
  * `solverProcessSize::Integer`: The number of solver processes of this participant using preCICE.
  * `communicator::Union{Ptr{Cvoid}, Ref{Cvoid}, Ptr{Nothing}}`: TODO ?
