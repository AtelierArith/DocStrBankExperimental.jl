Set the legend of the plot.

The plot legend is drawn using the extended text function GR.textext. You can use a subset of LaTeX math syntax, but will need to escape certain characters, e.g. parentheses. For more information see the documentation of GR.textext.

:param args: The legend strings

**Usage examples:**

.. code-block:: julia

```
julia> # Set the legends to "a" and "b"
julia> legend("a", "b")
```
