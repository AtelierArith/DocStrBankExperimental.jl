```
struct RampBi <: AbstractRampParameters
```

Parameters for both positive and negative ramping constraints for a node.

# Fields

  * **`up::TimeProfile`** is the maximum positive rate of change of a node.
  * **`down::TimeProfile`** is the maximum negative rate of change of a node.

!!! note
    The same profile is used for positive and negative bounds if you provide only a single `TimeProfile` as input.

