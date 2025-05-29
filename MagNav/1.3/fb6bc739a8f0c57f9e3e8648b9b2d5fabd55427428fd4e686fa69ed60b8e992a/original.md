```
euler2dcm(roll, pitch, yaw, order::Symbol = :body2nav)
```

Converts a (Euler) roll-pitch-yaw (`X`-`Y`-`Z`) right-handed body to navigation frame rotation (or the opposite rotation), to a DCM (direction cosine matrix). Yaw is synonymous with azimuth and heading here. If frame 1 is rotated to frame 2, then the returned DCM, when pre-multiplied, rotates a vector in frame 1 into frame 2. There are 2 use cases:

1. With `order = :body2nav`, the body frame is rotated in the standard

-roll, -pitch, -yaw sequence to the navigation frame. For example, if v1 is a 3x1 vector in the body frame [nose, right wing, down], then that vector rotated into the navigation frame [north, east, down] would be v2 = dcm * v1.

2. With `order = :nav2body`, the navigation frame is rotated in the standard

yaw, pitch, roll sequence to the body frame. For example, if v1 is a 3x1 vector in the navigation frame [north, east, down], then that vector rotated into the body frame [nose, right wing, down] would be v2 = dcm * v1.

Reference: Titterton & Weston, Strapdown Inertial Navigation Technology, 2004, Section 3.6 (pg. 36-41 & 537).

**Arguments:**

  * `roll`:  length-`N` roll  angle [rad], right-handed rotation about x-axis
  * `pitch`: length-`N` pitch angle [rad], right-handed rotation about y-axis
  * `yaw`:   length-`N` yaw   angle [rad], right-handed rotation about z-axis
  * `order`: (optional) rotation order {`:body2nav`,`:nav2body`}

**Returns:**

  * `dcm`: `3` x `3` x `N` direction cosine matrix [-]
