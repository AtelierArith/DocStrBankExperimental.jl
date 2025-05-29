Draw one or more step or staircase plots.

This function can receive one or more of the following:

  * x values and y values, or
  * x values and a callable to determine y values, or
  * y values only, with their indices as x values

:param args: the data to plot :param where: pre, mid or post, to decide where the step between two y values should be placed

**Usage examples:**

.. code-block:: julia     julia> # Create example data     julia> x = LinRange(-2, 2, 40)     julia> y = 2 .* x .+ 4     julia> # Plot x and y     julia> stairs(x, y)     julia> # Plot x and a callable     julia> stairs(x, x -> x^3 + x^2 + x)     julia> # Plot y, using its indices for the x values     julia> stairs(y)     julia> # Use next y step directly after x each position     julia> stairs(y, where="pre")     julia> # Use next y step between two x positions     julia> stairs(y, where="mid")     julia> # Use next y step immediately before next x position     julia> stairs(y, where="post")
