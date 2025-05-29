```julia
normalize_configuration!(state)

```

Project the configuration vector $q$ onto the configuration manifold.

For example:

  * for a part of $q$ corresponding to a revolute joint, this method is a no-op;
  * for a part of $q$ corresponding to a spherical joint that uses a unit quaternion

to parameterize the orientation of its successor with respect to its predecessor, `normalize_configuration!` will renormalize the quaternion so that it is indeed of unit length.

!!! warning



This method does not ensure that the configuration or velocity satisfy joint configuration or velocity limits/bounds.
