```
BoreDetector(CryRadius::Real, CryLength::Real, HoleRadius::Real)
```

construct and return a `bore-hole` detector of the given crystal dimensions:-

  * `CryRadius` : the detector crystal radius.
  * `CryLength` : the detector crystal length.
  * `HoleRadius` : the detector hole radius.

!!! warning
    `CryRadius` and `CryLength`, `HoleRadius` should be `positive` numbers, also  `CryRadius` should be greater than `HoleRadius`.

