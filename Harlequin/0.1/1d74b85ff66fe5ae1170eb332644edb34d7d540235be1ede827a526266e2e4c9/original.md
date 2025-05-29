A structure representing a quaternion.

Stripeline uses quaternions to encode rotations when generating pointings. The fields of `Quaternion` are:

  * `s`
  * `v1`
  * `v2`
  * `v3`

It is possible to multiply quaternions using the `*` operator. Constructors for rotation quaternions are provided by `qrotation_x`, `qrotation_y`, and `qrotation_z`.

`Quaternion` implements the `≈` binary relationship, in order to ease the implementation of tests.
