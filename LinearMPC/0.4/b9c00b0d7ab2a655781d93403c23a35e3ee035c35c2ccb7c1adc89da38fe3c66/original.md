```
compute_control(mpc,x;r,uprev)
```

For a given MPC `mpc` and state `x`, compute the optimal control action.  Optional arguments: 

  * `r` - reference value
  * `uprev` - previous control action

all of them defaults to zero.
