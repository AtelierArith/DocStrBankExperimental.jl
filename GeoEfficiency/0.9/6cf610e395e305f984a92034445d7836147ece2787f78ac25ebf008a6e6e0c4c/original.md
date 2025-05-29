```
Point(Height::Real, Rho::Real)
```

construct and return a `Point` source. The `Point` can be used as either a source by itself or an `anchor point` of a higher dimension source.

  * `Height` : point height relative to the detector surface.
  * `Rho` : point off-axis relative to the detector axis of symmetry.

!!! note
    Each detector type give different interpretation to the `height` as follow:-

      * for `CylDetector` the point source `height` is consider to be measured   from the detector `face surface`.
      * for `BoreDetector` the point source `height` is consider to be measured   from the `detector middle`, +ve value are above the detector center while -ve are below.
      * for `WellDetector` the point source `height` is considered to be measured   from the detector `hole surface`.

