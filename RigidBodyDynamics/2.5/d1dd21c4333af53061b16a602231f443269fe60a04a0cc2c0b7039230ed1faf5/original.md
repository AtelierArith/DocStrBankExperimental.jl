```julia
simulate(state0, final_time; ...)
simulate(
    state0,
    final_time,
    control!;
    Δt,
    stabilization_gains
)

```

Basic `Mechanism` simulation: integrate the state from time $0$ to `final_time` starting from the initial state `state0`. Return a `Vector` of times, as well as `Vector`s of configuration vectors and velocity vectors at these times.

Optionally, a function (or other callable) can be passed in as the third argument (`control!`). `control!` will be called at each time step of the simulation and allows you to specify joint torques given the time and the state of the `Mechanism`. It should look like this:

```julia
function control!(torques::AbstractVector, t, state::MechanismState)
    rand!(torques) # for example
end
```

The integration time step can be specified using the `Δt` keyword argument (defaults to `1e-4`).

The `stabilization_gains` keyword argument can be used to set PD gains for Baumgarte stabilization, which can be used to prevent separation of non-tree (loop) joints. See Featherstone (2008), section 8.3 for more information. There are several options for specifying gains:

  * `nothing` can be used to completely disable Baumgarte stabilization.
  * Gains can be specifed on a per-joint basis using any `AbstractDict{JointID, <:RigidBodyDynamics.PDControl.SE3PDGains}`, which maps the `JointID` for the non-tree joints of the mechanism to the gains for that joint.
  * As a special case of the second option, the same gains can be used for all joints by passing in a `RigidBodyDynamics.CustomCollections.ConstDict{JointID}`.

The [`default_constraint_stabilization_gains`](@ref) function is called to produce the default gains, which use the last option.

Uses `MuntheKaasIntegrator`. See [`RigidBodyDynamics.OdeIntegrators.MuntheKaasIntegrator`](@ref) for a lower level interface with more options.
