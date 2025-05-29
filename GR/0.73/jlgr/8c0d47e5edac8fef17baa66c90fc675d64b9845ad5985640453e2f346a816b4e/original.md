Create a new figure with the given settings.

Settings like the current colormap, title or axis limits as stored in the current figure. This function creates a new figure, restores the default settings and applies any settings passed to the function as keyword arguments.

**Usage examples:**

.. code-block:: julia

```
julia> # Restore all default settings
julia> figure()
julia> # Restore all default settings and set the title
julia> figure(title="Example Figure")
```
