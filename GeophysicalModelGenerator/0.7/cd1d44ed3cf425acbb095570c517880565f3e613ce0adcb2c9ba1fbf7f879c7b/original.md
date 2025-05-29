```
Phase = compute_phase(Phase, Temp, X, Y, Z, s::LithosphericPhases, Ztop)
```

or

```
Phase = compute_phase(Phase, Temp, Grid::AbstractGeneralGrid, s::LithosphericPhases)
```

This copies the layered lithosphere onto the Phase matrix.

# Parameters

  * Phase - Phase array
  * Temp  - Temperature array
  * X     - x-coordinate array (consistent with Phase and Temp)
  * Y     - y-coordinate array (consistent with Phase and Temp)
  * Z     - Vertical coordinate array (consistent with Phase and Temp)
  * s     - LithosphericPhases
  * Ztop  - Vertical coordinate of top of model box
  * Grid  - Grid structure (usually obtained with read*LaMEM*inputfile)
