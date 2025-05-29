```
is_system_in_relative_motion(lsid::Int,ls::RigidBodyMotion) -> Bool
```

Returns `true` if the linked system with ID `lsid` is in relative motion, i.e., if one or more of the joints (not connected to the inertial system) returns `true` for the function `ismoving(joint)`.
