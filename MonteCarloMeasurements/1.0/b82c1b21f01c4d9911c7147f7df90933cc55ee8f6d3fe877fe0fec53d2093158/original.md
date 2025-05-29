```
struct Workspace{T1, T2, T3, T4, T5, T6}
```

# Arguments:

  * `simple_input`: Input object `f` will be called with, does not contain any particles
  * `simple_result`: Simple output from `f` without particles
  * `result`: Complete output of `f` including particles
  * `buffersetter`: Helper function to shift data between objects
  * `resultsetter`: Helper function to shift data between objects
  * `f`: Function to call
  * `N`: Number of particles
