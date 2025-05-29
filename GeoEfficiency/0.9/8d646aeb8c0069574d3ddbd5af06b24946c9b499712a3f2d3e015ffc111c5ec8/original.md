```
WellDetector(CryRadius::Real, CryLength::Real, HoleRadius::Real, HoleDepth::Real)
```

construct and return a `Well-Type` detector of the given crystal dimensions:-

  * `CryRadius` : the detector crystal radius.
  * `CryLength` : the detector crystal length.
  * `HoleRadius` : the detector hole radius.
  * `HoleDepth` : the detector hole length.

!!! warning
    all arguments should be `positive` numbers, also  `CryRadius` should be greater than `HoleRadius` and  `CryLength` should be greater than  `HoleDepth`.

