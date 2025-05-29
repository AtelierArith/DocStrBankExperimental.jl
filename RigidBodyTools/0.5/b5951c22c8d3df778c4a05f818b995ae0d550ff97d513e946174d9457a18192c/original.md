```
init_motion_state(bl::BodyList,ls::RigidBodyMotion[;tinit = 0.0])
```

Initialize the global linked system state vector, using the prescribed motions for constrained degrees of freedom to initialize the position components (evaluated at `tinit`, which by default is 0). The other degrees of freedom are initialized to zero, and can be set manually.
