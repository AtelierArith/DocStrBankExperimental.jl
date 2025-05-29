```julia
dynamics!(result, state; ...)
dynamics!(result, state, torques; ...)
dynamics!(
    result,
    state,
    torques,
    externalwrenches;
    stabilization_gains
)

```

Compute the joint acceleration vector $\dot{v}$ and Lagrange multipliers $\lambda$ that satisfy the joint-space equations of motion

$$
M(q) \dot{v} + c(q, v, w_\text{ext}) = \tau - K(q)^{T} \lambda
$$

and the constraint equations

$$
K(q) \dot{v} = -k
$$

given joint configuration vector $q$, joint velocity vector $v$, and (optionally) joint torques $\tau$ and external wrenches $w_\text{ext}$.

The `externalwrenches` argument can be used to specify additional wrenches that act on the `Mechanism`'s bodies.

The `stabilization_gains` keyword argument can be used to set PD gains for Baumgarte stabilization, which can be used to prevent separation of non-tree (loop) joints. See Featherstone (2008), section 8.3 for more information. There are several options for specifying gains:

  * `nothing` can be used to completely disable Baumgarte stabilization.
  * Gains can be specifed on a per-joint basis using any `AbstractDict{JointID, <:RigidBodyDynamics.PDControl.SE3PDGains}`, which maps the `JointID` for the non-tree joints of the mechanism to the gains for that joint.
  * As a special case of the second option, the same gains can be used for all joints by passing in a `RigidBodyDynamics.CustomCollections.ConstDict{JointID}`.

The [`default_constraint_stabilization_gains`](@ref) function is called to produce the default gains, which use the last option.
