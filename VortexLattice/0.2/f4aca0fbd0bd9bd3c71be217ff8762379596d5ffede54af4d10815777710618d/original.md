```
nonlinear_analysis!(system)
```

Perform a nonlinear analysis on the system. This assumes that reference and freestream are already contained in the system

# Arguments

  * `system::System`: The system to perform the analysis on
  * `max_iter`: The maximum number of iterations to perform, default 1
  * `tol`: The tolerance for convergence (based on absolute difference in Γ), default 1
  * `damping`: The damping factor for the iteration default 0.1
  * `kwargs...`: Additional keyword arguments for steady analysis
