```
zero_joint(ls::RigidBodyMotion[;dimfcn=position_and_vel_dimension])
```

Create a vector of zeros for some aspect of the state of the linked system(s) `ls`, based on the argument `dimfcn`. By default, it uses `position_and_vel_dimension` and creates a zero vector sized according to the state of the joint. Alternatively, one can use `position_dimension`, `constrained_dimension`, `unconstrained_dimension`, or `exogenous_dimension`.
