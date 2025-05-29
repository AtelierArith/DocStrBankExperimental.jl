Calculate the configuration along the path, using the parameter t

  * path      - an initialized path
  * $t$         - length measure where $0 \leq t <$ [`dubins_path_length`](@ref)(path)
  * return    - tuple containing non-zero error code if 't' is not in the correct range and the configuration result $[x, y, \theta]$
