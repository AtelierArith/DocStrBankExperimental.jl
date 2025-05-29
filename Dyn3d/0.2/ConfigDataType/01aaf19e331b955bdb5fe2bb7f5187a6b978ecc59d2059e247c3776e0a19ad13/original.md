```
Motions(type::String, parameters::Vector{Float64})
```

A structure representing active motion of a joint, allowing different types of motion, can be time-dependent.

## Fields

  * `motion_type`: Allow choices of "hold", "velocity*const", "velocity*linear", "oscillatory", "ramp*1", "ramp*2"
  * `motion_params`: Numerical parameters provided to describe the motion

## Constructors

  * `Motions(): Provide no active motion`
  * `Motions("hold", [qJ])`: Hold the joint at constant qJ and vJ=0
  * `Motions("velocity_const",[qJ,vJ])`: Specify constant vJ of this joint with initial angle qJ
  * `Motions("velocity_linear",[qJ,vJ,aJ])`: Specify constant acceleration aJ of this joint with   initial angle qJ and initial angular velocity vJ, and the specified angular velocity is linear
  * `Motions("oscillatory",[amp,freq,phase])` specify a oscillatory motion through   $qJ = amp*cos(2π*freq*t+phase)$
  * `Motions("ramp_1",[a,t₁,t₂,t₃,t₄])`: Describes a ramp motion in [^1]
  * `Motions("ramp_2",[a])`: Describes a decelerating motion with an initial velocity

[^1]: Eldredge, Jeff, Chengjie Wang, and Michael Ol. "A computational study of a canonical pitch-up,

pitch-down wing maneuver." In 39th AIAA fluid dynamics conference, p. 3687. 2009.

## Functions

  * `(m::Motions)(t)`: Evalutes the motion type at time t, return joint angle qJ and   velocity vJ
