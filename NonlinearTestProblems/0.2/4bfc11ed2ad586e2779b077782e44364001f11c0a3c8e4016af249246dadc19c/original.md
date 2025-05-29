`starting_point(problem)`

`starting_point(problem, α)`

Recommended starting point of a test problem for methods that need one (eg quasi-Newton). Usually taken from the literature that defines a problem, and should be “difficult”.

When used with a (positive real) argument `α`, the method should attempt to make it more difficult (eg move away further from the root).

!!! note
    A default method is provided for the latter, problems just need to implement the single-argument version.

