```
Qc = d2c(sys::AbstractStateSpace{<:Discrete}, Qd::AbstractMatrix; opt=:o)
```

Resample discrete-time covariance matrix belonging to `sys` to the equivalent continuous-time matrix.

The method used comes from theorem 5 in the reference below.

If `opt = :c`, the matrix is instead assumed to be a cost matrix for an LQR problem.

Ref: Discrete-time Solutions to the Continuous-time Differential Lyapunov Equation With Applications to Kalman Filtering Patrik Axelsson and Fredrik Gustafsson
