This type encodes constraints as the following additional penalty for an objective function:

$p(x) = \sum^n_{i=1} r_i max(0, g_i(x))^2$

where $r_i$ is a penalty value for $i$th constraint, and $g_i(x)$ is an inequality constraint. The equality constraints $h_i(x) = 0$ are transformed to inequality constraints as follows:

$h(x) - \epsilon  \leq 0$

The constructor takes following arguments:

  * `penalties`: a vector of penalty values per constraint (optional)
  * `lx`: a vector of value lower bounds
  * `ux`: a vector of value upper bounds
  * `lc`: a vector of constrain function lower bounds
  * `uc`: a vector of constrain function upper bounds
  * `c`: a constraint function which returns a constrain values
