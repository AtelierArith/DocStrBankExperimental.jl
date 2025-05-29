Save the current figure to a file.

This function draw the current figure using one of GR's workstation types to create a file of the given name. Which file types are supported depends on the installed workstation types, but GR usually is built with support for .png, .jpg, .pdf, .ps, .gif and various other file formats.

:param filename: the filename the figure should be saved to

**Usage examples:**

.. code-block:: julia

```
julia> # Create a simple plot
julia> x = 1:100
julia> plot(x, 1 ./ (x .+ 1))
julia> # Save the figure to a file
julia> savefig("example.png")
```
