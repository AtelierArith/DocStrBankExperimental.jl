```
launch!(p::Path; kwargs...)
```

Add a coplanar-waveguide "launcher" structure to `p`.

If `p` is empty, start the path with a launcher; otherwise, terminate with a launcher.

This method exists mainly for use in demonstrations. The launcher design is not optimized for microwave properties.

Keywords:

  * `extround = 5.0μm`: Rounding of the "back" of the pad and external ground plane "behind" the launcher
  * `trace0 = 300.0μm`: Trace width of the pad
  * `trace1 = 10.0μm`: Trace width of the launched CPW
  * `gap0 = 150.0μm`: Gap width of the pad
  * `gap1 = 6.0μm`: Gap width of the final CPW
  * `flatlen = 250.0μm`: Length of the pad
  * `taperlen = 250.0μm`: Length of the taper between pad and launched CPW
