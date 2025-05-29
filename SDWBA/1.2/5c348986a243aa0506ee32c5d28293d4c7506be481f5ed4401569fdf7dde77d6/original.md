Rotate the scatterer in space, returning a rotated copy.

#### Parameters

  * `roll` : Angle to roll the scatterer, in degrees. Defaults to 0.
  * `tilt` : Angle to tilt the scatterer, in degrees. Defaults to 0.
  * `yaw` : Angle to yaw the scatterer, in degrees. Defaults to 0.

#### Returns

A Scatterer with the same shape and properties, but a new orientation.

The roll, tilt, and yaw refer to rotations around the x, y, and z axes, respectively. They are applied in that order.
