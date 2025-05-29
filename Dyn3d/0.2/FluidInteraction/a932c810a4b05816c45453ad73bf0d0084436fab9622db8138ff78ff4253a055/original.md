```
AcquireBodyGridKinematics(bd::BodyDyn, bgs::Vector{BodyGrid})
```

Given updated bd structure, which contains 3d bs[i].x*i in inertial frame and 6d bs[i].v of each body in the body local frame, return 3d linear q*i and v_i of each body point in the inertial frame.
