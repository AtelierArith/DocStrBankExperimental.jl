R is defined as the rotation matrix in [1, Eqs.(3), (4)]. Please check if it is the transpose of the rotation matrix defined in FSimZoo multicopters.

# Notes

When obtaining R*d*dot and ω*d*dot, one may need to obtain the derivative of b*3*d, which contains e*v. This implies that we need to obtain acceleration (a=v*dot) to get the control input f (total thrust), but the acceleration is induced by f, which results in algebraic loop.

Therefore, the a_d and higher-order derivatives are obtained from derivative filters.
