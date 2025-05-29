```
make_theta0s(theta0::T, ball_radius::T, pdf, nwalkers;
                  ball_radius_halfing_steps=7, # make the ball smaller this often
                  ntries=100*nwalkers, # how many tries per pall radius
                  hasblob=false) where T
```

Tries to find theta0s with nonzero density within a ball from theta0.  To be used with `emcee`.

Example

```
pdf = x-> -sum(x.^2)
nwalkers = 100
samples = emcee(pdf, make_theta0s([0.0, 0.0], [0.1, 0.1], pdf, nwalkers), nburnin=0, use_progress_meter=false);
```
