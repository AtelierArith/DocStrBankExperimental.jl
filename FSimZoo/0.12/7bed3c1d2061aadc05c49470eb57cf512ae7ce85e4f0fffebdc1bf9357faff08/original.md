# References

  * Controller (it may be modified in this implementation)

[1] G. P. Falconi and F. Holzapfel, “Adaptive Fault Tolerant Control Allocation for a Hexacopter System,” Proc. Am. Control Conf., vol. 2016-July, pp. 6760–6766, 2016.

  * Reference model (e.g., xd, vd, ad, ad*dot, ad*ddot)

[2] S. J. Su, Y. Y. Zhu, H. R. Wang, and C. Yun, “A Method to Construct a Reference Model for Model Reference Adaptive Control,” Adv. Mech. Eng., vol. 11, no. 11, pp. 1–9, 2019.

# NOTICE

  * (Tracking control) Add the argument `pos_cmd_func` (a function of time such that (t) -> position(t) ∈ ℝ^3) of constructor,

please do not add the argument `pos_cmd` in the inner function of `Dynamics!(env::BacksteppingPositionController)`.

  * (Set-point control) Do not add the argument `pos_cmd_func` (a function of time such that (t) -> position(t) ∈ ℝ^3) of constructor,

please add the argument `pos_cmd` in the inner function of `Dynamics!(env::BacksteppingPositionController)`.
