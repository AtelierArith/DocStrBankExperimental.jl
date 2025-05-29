```
`import_vsp(comp::vsp.VSPComponent; geomType::String="", optargs...)
```

Imports properties from OpenVSP component to VortexLattice objects. Importing prop and duct geometries are under development.

**Arguments**

  * `comp::VSPGeom.VSPComponent`: Single `VSPGeom.VSPComponent` object
  * `geomType::String` : Geometry type may be one of - `wing`, `fuselage`, `prop`, `duct`
  * `optargs` : Optional arguments that are passed into grid*to*surface_panels() called inside

**Returns**

  * `grid`: Array with dimensions (3, i, j) containing the panel corners
  * `surface`: Array with dimensions (i, j) containing generated panels
