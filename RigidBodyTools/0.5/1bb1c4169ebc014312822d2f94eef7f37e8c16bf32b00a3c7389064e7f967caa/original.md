```
zero_joint(joint::Joint[;dimfcn=position_and_vel_dimension])
```

Create a vector of zeros for different aspects of the joint state, based on the argument `dimfcn`. By default, it uses `position_and_vel_dimension` and creates a zero vector sized according to the the position of the joint and the parts of the joint velocity that must be advanced (from acceleration). Alternatively, one can use `position_dimension`, `constrained_dimension`, `unconstrained_dimension`, or `exogenous_dimension`.
