```
XPRSchgobjsense(prob, objsense)::prob
```

Changes the problem's objective function sense to minimize or maximize.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `objsense::XPRSObjSense`: `XPRS_OBJ_MINIMIZE` to change into a minimization, or `XPRS_OBJ_MAXIMIZE` to change into maximization problem.

# Return value

  * `prob::XPRSprob`: The current problem.

See also the documentation of the correponding function [XPRSchgobjsense](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSchgobjsense.html) in the C API.
