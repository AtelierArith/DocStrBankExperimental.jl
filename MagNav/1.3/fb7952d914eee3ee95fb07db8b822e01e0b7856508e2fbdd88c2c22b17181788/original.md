```
dcm2euler(dcm, order::Symbol = :body2nav)
```

Converts a DCM (direction cosine matrix) to yaw, pitch, and roll Euler angles. Yaw is synonymous with azimuth and heading here. There are 2 use cases:

1. With `order = :body2nav`, the provided DCM is assumed to rotate from the

body frame in the standard -roll, -pitch, -yaw sequence to the navigation frame. For example, if v1 is a 3x1 vector in the body frame [nose, right wing, down], then that vector rotated into the navigation frame [north, east, down] would be v2 = dcm * v1.

2. With `order = :nav2body`, the provided DCM is assumed to rotate from the

navigation frame in the standard yaw, pitch, roll sequence to the body frame. For example, if v1 is a 3x1 vector in the navigation frame [north, east, down], then that vector rotated into the body frame [nose, right wing, down] would be v2 = dcm * v1.

Reference: Titterton & Weston, Strapdown Inertial Navigation Technology, 2004, Section 3.6 (pg. 36-41 & 537).

**Arguments:**

  * `dcm`:   `3` x `3` x `N` direction cosine matrix [-]
  * `order`: (optional) rotation order {`:body2nav`,`:nav2body`}

**Returns:**

  * `roll`:  length-`N` roll  angle [rad], right-handed rotation about x-axis
  * `pitch`: length-`N` pitch angle [rad], right-handed rotation about y-axis
  * `yaw`:   length-`N` yaw   angle [rad], right-handed rotation about z-axis
