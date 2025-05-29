```
IpoptCriteria
```

This convergence criteria uses a scaled version of the Karush-Kuhn-Tucker (KKT) residual and maximum infeasibility to assess convergence. This scaled KKT residual is used in the IPOPT nonlinear programming solver as explained in [this paper](http://cepac.cheme.cmu.edu/pasilectures/biegler/ipopt.pdf). More details are given in [`assess_convergence!`](@ref). 
