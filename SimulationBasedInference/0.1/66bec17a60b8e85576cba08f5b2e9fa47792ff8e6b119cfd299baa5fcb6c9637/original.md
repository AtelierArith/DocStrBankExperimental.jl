```
SimulatorObservable{N,outputType<:SimulatorOutput,funcType,coordsType} <: Observable{outputType}
```

Represents a named "observable" that stores output from a simulator. `obsfunc` defines a mapping from the simulator state to the observed quantity. The type and implementation of `output` determines how the samples are stored. The simplest output type is `Transient` which simply maintains a pointer to the last observed output.
