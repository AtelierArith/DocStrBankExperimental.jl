```julia
zero_configuration!(state)

```

'Zero' the configuration vector $q$. Invalidates cache variables.

Note that when the `Mechanism` contains e.g. quaternion-parameterized joints, $q$ may not actually be set to all zeros; the quaternion part of the configuration vector would be set to identity. The contract is that each of the joint transforms should be an identity transform.
