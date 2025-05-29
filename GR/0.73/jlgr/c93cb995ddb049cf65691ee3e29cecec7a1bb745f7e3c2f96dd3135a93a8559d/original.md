Set the x-axis label.

The axis labels are drawn using the extended text function GR.textext. You can use a subset of LaTeX math syntax, but will need to escape certain characters, e.g. parentheses. For more information see the documentation of GR.textext.

:param x_label: the x-axis label

**Usage examples:**

.. code-block:: julia

```
julia> # Set the x-axis label to "x"
julia> xlabel("x")
julia> # Clear the x-axis label
julia> xlabel("")
```
