```
child_joints_of_body(bodyid,ls::RigidBodyMotion)
```

Return the indices (if any) of the child joints of body `bodyid` in system `ls`. This function also accepts `bodyid = 0`, and returns the indices of joints that connect bodies to the inertial coordinate system.
