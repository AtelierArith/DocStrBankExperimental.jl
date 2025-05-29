Generate a path with a specified word from an initial configuratioon to a target configuration, with a specified turning radius

  * $q_0$       - a configuration specified by a 3-element vector $x$, $y$, $\theta$
  * $q_1$       - a configuration specified by a 3-element vector $x$, $y$, $\theta$
  * $\rho$     - turning radius of the vehicle
  * path_type - the specified path type to use
  * return    - tuple (error code, dubins path). If error code != 0, then `nothing` is returned as the second argument
