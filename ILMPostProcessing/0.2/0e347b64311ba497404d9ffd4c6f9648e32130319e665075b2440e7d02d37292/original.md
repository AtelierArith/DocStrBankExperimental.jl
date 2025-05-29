compute_streakline(u,v,X₀::Vector,t[;τmin = t-3.0, dtstreak=0.01,dttraj=0.001]) -> Vector, Vector

Calculate a streakline at time `t` for a velocity field `u` and `v`, based on an injection point `X₀`. The end of the streakline is set by `τmin`, the earliest time at which a particle passed through the injection point. It defaults to 3 time units before the current instant `t`. The time step size `dtstreak` sets the resolution of the streakline (i.e., how often the particles are sampled along the streakline). It returns arrays of the x and y coordinates of the streakline.
