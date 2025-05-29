This type encodes constraints as the following additional penalty for an objective function:

$p(x) = f_{worst} + \sum^n_{i=1} |g_i(x)|$

if $x$ is not feasible, otherwise no penalty is applied.

The constructor takes following arguments:

  * `lx`: a vector of value lower bounds
  * `ux`: a vector of value upper bounds
  * `lc`: a vector of constrain function lower bounds
  * `uc`: a vector of constrain function upper bounds
  * `c`: a constraint function which returns a constrain values
