```
add_fault!(Phase, Temp, Grid::AbstractGeneralGrid;
    Start=(20,100), End=(10,80),
    Fault_thickness=10.0,
    Depth_extent=nothing,
    DipAngle=0e0,
    phase=ConstantPhase(1),
    T=nothing,
    cell=false)
```

Adds a fault to the given 3D grid by modifying the `Phase` and `Temp` arrays. For a 2D grid, use `add_box` instead.

# Arguments

  * `Phase`: Phase array
  * `Temp`: Temp array
  * `Grid`: The grid on which the fault is to be added.
  * `Start`: Tuple representing the starting coordinates of the fault (X, Y).
  * `End`: Tuple representing the ending coordinates of the fault (X, Y).
  * `Fault_thickness`: Thickness of the fault.
  * `Depth_extent`: Depth extent of the fault. If `nothing`, the fault extends through the entire domain.
  * `DipAngle`: Dip angle of the fault.
  * `phase`: Phase to be assigned to the fault.
  * `T`: Temperature to be assigned to the fault. If `nothing`, the temperature is not modified.

# Example

```julia
add_fault!(Phase, Temp, Grid;
        Start=(20,100), End=(10,80),
        Fault_thickness=10.0,
        Depth_extent=(-25.0, 0.0),
        DipAngle=-10.0,
        phase=ConstantPhase(1)
        )
```
