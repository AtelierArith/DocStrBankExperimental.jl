```
DroneSurveillancePOMDP{M} <: POMDP{DSState, Int64, Int64}
```

# Fields

  * `size::Tuple{Int64, Int64} = (5,5)` size of the grid world
  * `region_A::DSPos = [1, 1]` first region to survey, initial state of the quad
  * `region_B::DSPos = [size[1], size[2]]` second region to survey
  * `fov::Tuple{Int64, Int64} = (3, 3)` size of the field of view of the drone
  * `agent_policy::Symbol = :restricted` policy of the other agent
  * `camera::M = QuadCam()` observation model, choose between perfect camera and quad camera
  * `terminal_state::DSState = DSState([-1, -1], [-1, -1])` a sentinel state to encode terminal states
  * `discount_factor::Float64 = 0.95` the discount factor
