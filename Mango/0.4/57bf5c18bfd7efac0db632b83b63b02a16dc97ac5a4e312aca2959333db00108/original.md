```
calculate_communication(communication_sim::CommunicationSimulation, clock::Clock, messages::Vector{MessagePackage})::CommunicationSimulationResult
```

Calculate the communication using the specific communication simulation type. the current simulation time `clock` and the message which shall be sent in this step `messages`
