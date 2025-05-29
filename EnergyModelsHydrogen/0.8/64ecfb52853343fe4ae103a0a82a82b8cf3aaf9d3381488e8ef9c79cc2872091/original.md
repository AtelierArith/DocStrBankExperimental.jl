```
struct RampDown <: AbstractRampParameters
```

Parameters for negative ramping constraints for a node.

# Fields

  * **`down::TimeProfile`** is the maximum negative rate of change of a node.
