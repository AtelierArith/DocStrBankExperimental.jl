```julia
primitive type Stepsize <: Enum{Int32} 32
```

Public type used to specify the stepping scheme of the path-following schemes. For more information see the [interior-point section](@ref path-following-theory) in the documentation.

# Available Options

  * `SHORT`:   Regular update of the paramter t.
  * `LONG`:   Larger update of the parameter t if iterate fulfill approximate centering conditon.   Results in line-search for application of update on the iterate x.
  * `ADAPTIVE`:   Same as the long stepping, but the factor for the larger update is adaptively changed   depending on how many steps it required to fulfill the approximate centering condition.
