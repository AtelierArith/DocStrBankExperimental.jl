```julia
principal_value!(state)

```

Applies the principal*value functions from [Rotations.jl](https://github.com/FugroRoames/Rotations.jl/blob/d080990517f89b56c37962ad53a7fd24bd94b9f7/src/principal*value.jl) to joint angles. This currently only applies to `SPQuatFloating` joints.

For example:

  * for a part of $q$ corresponding to a revolute joint, this method is a no-op;
  * for a part of $q$ corresponding to a `SPQuatFloating` joint this function applies

`principal_value the orientation.
