Set the plot title.

The plot title is drawn using the extended text function GR.textext. You can use a subset of LaTeX math syntax, but will need to escape certain characters, e.g. parentheses. For more information see the documentation of GR.textext.

:param title: the plot title

**Usage examples:**

.. code-block:: julia

```
julia> # Set the plot title to "Example Plot"
julia> title("Example Plot")
julia> # Clear the plot title
julia> title("")
```
