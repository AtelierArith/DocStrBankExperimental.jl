```
CylDetector(CryRadius::Real, CryLength::Real)
```

construct and return a `cylindrical` detector of the given crystal dimensions:-

  * `CryRadius` : the detector crystal radius.
  * `CryLength` : the detector crystal length.

!!! warning
    both `CryRadius` and `CryLength` should be `positive`, while `CryLength` can also be set to **`zero`**.

