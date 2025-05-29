```
RotationRule(order, motion, radian, main, extrinsic)
```

Creates a rule for the ellipsoidal rotation

  * order     - sequence of three axes by which the rotations are made; e.g. `:ZXZ`
  * motion    - inform for each of the three rotations if it is clockwise (`:CW`) or             counterclockwise (`:CCW`). Right-hand rule: motion defined looking             towards the negative direction of the axis
  * radian    - `true` if the input angles are in radians or `false` if in degrees
  * main      - inform if the main semiaxis is `:x` or `:y`
  * extrinsic - `true` if rotation is extrinsic or `false` if it is intrinsic

## Example

Rotation rule to reproduce GSLIB rotation

```julia
rule = RotationRule(:ZXY,[:CW,:CCW,:CCW],false,:y,false)
```

## Conventions

Some rotation conventions built-in:

  * `:TaitBryanExtr` => Extrinsic right-handed rotation by the ZXY axes
  * `:TaitBryanIntr` => Intrinsic right-handed rotation by the ZXY axes
  * `:EulerExtr`     => Extrinsic right-handed rotation by the ZXZ axes
  * `:EulerIntr`     => Intrinsic right-handed rotation by the ZXZ axes
  * `:GSLIB`         => GSLIB software rotation convention
  * `:Leapfrog`      => Leapfrog software rotation convention
  * `:Datamine`      => Datamine software rotation convention, axes order ZXZ
  * `:Datamine313`   => Datamine software rotation convention, axes order ZXZ
  * `:Datamine321`   => Datamine software rotation convention, axes order ZYX
  * `:Datamine312`   => Datamine software rotation convention, axes order ZXY
  * `:Datamine323`   => Datamine software rotation convention, axes order ZYZ
