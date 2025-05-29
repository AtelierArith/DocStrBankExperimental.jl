R is defined as the rotation matrix in [1, Eqs.(3), (4)]. Please check if it is the transpose of the rotation matrix defined in FSimZoo multicopters.

# Notes

When implementing geometric controller, you need to access the acceleration and jerk, which requires the knowledge of dynamics. In general, it may be inaccurate. Instead, here, I implemented geometric controller with observers (filters) to estimate them.

For the ideal case, see `Command_Ideal(controller::GeometricTrackingController, args...; kwargs...)`.
