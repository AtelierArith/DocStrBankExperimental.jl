```
BinaryInvestment <: Investment
```

Binary investment in a given capacity with binary variables. The chosen capacity within an investment period is given by the field `cap`.

Binary investments introduce one binary variable for each investment period.

# Fields

  * **`cap::TimeProfile`** is the capacity used for the binary investments. These investments come in addition to the existing capacity.
