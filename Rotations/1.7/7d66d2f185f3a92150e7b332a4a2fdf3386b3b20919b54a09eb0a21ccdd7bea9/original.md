```
principal_value(R::Rotation{3})
```

**Background:** All non `RotMatrix` rotation types can represent the same `RotMatrix` in two or more ways. Sometimes a particular set of numbers is better conditioned (e.g. `MRP`) or obeys a particular convention (e.g. `AngleAxis` has non-negative rotation). In order to preserve differentiability it is necessary to allow rotation representations to travel slightly away from the nominal domain; this is critical for applications such as optimization or dynamics.

This function takes a rotation type (e.g. `QuatRotation`, `RotXY`) and outputs a new rotation of the same type that corresponds to the same `RotMatrix`, but that obeys certain conventions or is better conditioned. The outputs of the function have the following properties:

  * all angles are between between `-pi` to `pi` (except for `AngleAxis` which is between `0` and `pi`).
  * all `QuatRotation have non-negative real part
  * the components of all `MRP` have a norm that is at most 1.
  * the `RotationVec` rotation is at most `pi`
