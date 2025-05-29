```
Structure that holds a GeoUnit parameter, and encodes the units and whether it is dimensional or not in the name.

Having that is useful, as non-dimensionalization removes the units from a number and we thus no longer know how to transfer it back to the correct units.
With the GeoUnit struct, this information is retained, and we can thus redimensionalize it at a later StepRange
```
