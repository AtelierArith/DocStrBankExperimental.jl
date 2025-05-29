```
ShootingInverseRetraction <: ApproximateInverseRetraction
```

Approximating the inverse of a retraction using the shooting method.

This implementation of the shooting method works by using another inverse retraction to form the first guess of the vector. This guess is updated by shooting the vector, guessing the vector pointing from the shooting result to the target point, and transporting this vector update back to the initial point on a discretized grid. This process is repeated until the norm of the vector update falls below a specified tolerance or the maximum number of iterations is reached.

# Fields

  * `retraction::AbstractRetractionMethod`: The retraction whose inverse is approximated.
  * `initial_inverse_retraction::AbstractInverseRetractionMethod`: The inverse retraction used   to form the initial guess of the vector.
  * `vector_transport::AbstractVectorTransportMethod`: The vector transport used to transport   the initial guess of the vector.
  * `num_transport_points::Int`: The number of discretization points used for vector   transport in the shooting method. 2 is the minimum number of points, including just the   endpoints.
  * `tolerance::Real`: The tolerance for the shooting method.
  * `max_iterations::Int`: The maximum number of iterations for the shooting method.
