FlightPathController as specified in chapter six of the PhD thesis of Uwe Fechner.

Main inputs are calls to the functions:

  * on*control*command()
  * on*est*sys_state()

Main output is the set value of the steering u_s, returned by the method:

  * calc_steering()

Once per time step the method

  * on_timer

must be called.

See also: docs/flight*path*controller*I.png and docs/flight*path*controller*II.png and docs/flight*path*controller_III.png
