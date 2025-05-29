Customize the string of the X and Y axes tick labels.

The labels of the tick axis can be defined through a function with one argument (the numeric value of the tick position) and returns a string, or through an array of strings that are located sequentially at X = 1, 2, etc.

:param s: function or array of strings that define the tick labels.

**Usage examples:**

.. code-block:: julia

```
julia> # Label the range (0-1) of the Y-axis as percent values
julia> yticklabels(p -> Base.Printf.@sprintf("%0.0f%%", 100p))
julia> # Label the X-axis with a sequence of strings
julia> xticklabels(["first", "second", "third"])
```
