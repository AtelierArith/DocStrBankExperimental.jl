```
DeviceRAModel{D <: PSY.Device, B <: AbstractRAFormulation}
```

# Arguments

  * D <: PSY.Device: Device type

      * `formulation::SiennaPRASInterface.AbstractRAFormulation`: Formulation containing configuration

A DeviceRAModel, like a DeviceModel in PowerSimulations, assigns a type of Component to a specific formulation. Unlike Sienna, we put configuration information in the formulation itself.
