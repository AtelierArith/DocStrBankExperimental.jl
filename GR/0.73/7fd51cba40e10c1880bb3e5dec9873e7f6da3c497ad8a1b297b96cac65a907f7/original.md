```
setwsviewport(xmin::Real, xmax::Real, ymin::Real, ymax::Real)
```

Define the size of the workstation graphics window in meters.

**Parameters:**

`xmin` :     The left horizontal coordinate of the workstation viewport. `xmax` :     The right horizontal coordinate of the workstation viewport. `ymin` :     The bottom vertical coordinate of the workstation viewport. `ymax` :     The top vertical coordinate of the workstation viewport.

`setwsviewport` places a workstation window on the display of the specified size in meters. This command allows the workstation window to be accurately sized for a display or hardcopy device, and is often useful for sizing graphs for desktop publishing applications.
