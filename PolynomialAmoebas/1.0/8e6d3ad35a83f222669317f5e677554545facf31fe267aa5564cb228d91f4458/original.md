```
MembershipTestResult{T, N}
```

**Fields**

  * `successfull::Bool`
  * `tries::Int` The number of times Newton's method was started
  * `converged_iterations::Int` Number iterations needed in a successfull iteration. If the test was not successfull `imax` is the maximal number of iterations.
  * `startvalue::SVector{N, T}` The start value of the successfull iteration. Otherwise a random value.
  * `solution::SVector{N, T}` The solution value of the successfull iteration. Otherwise a random value.
