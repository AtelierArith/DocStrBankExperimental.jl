Generate a path from an initial configuration to a target configuration with a specified maximum turning radius

A configuration is given by $[x, y, \theta]$, where $\theta$ is in radians,

  * $q_0$        - a configuration specified by a 3-element vector $[x, y, \theta]$
  * $q_1$        - a configuration specified by a 3-element vector $[x, y, \theta]$
  * $\rho$      - turning radius of the vehicle
  * return    - tuple (error code, dubins path). If error code != 0, then `nothing` is returned as the second argument
