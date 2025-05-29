Set the limits for the y-axis.

The y-axis limits can either be passed as individual arguments or as a tuple of (**y_min**, **y_max**). Setting either limit to **nothing** will cause it to be automatically determined based on the data, which is the default behavior.

:param y*min: 	- the y-axis lower limit, or 	- **nothing** to use an automatic lower limit, or 	- a tuple of both y-axis limits :param y*max: 	- the y-axis upper limit, or 	- **nothing** to use an automatic upper limit, or 	- **nothing** if both y-axis limits were passed as first argument :param adjust: whether or not the limits may be adjusted

**Usage examples:**

.. code-block:: julia

```
julia> # Set the y-axis limits to -1 and 1
julia> ylim((-1, 1))
julia> # Reset the y-axis limits to be determined automatically
julia> ylim()
julia> # Reset the y-axis upper limit and set the lower limit to 0
julia> ylim((0, nothing))
julia> # Reset the y-axis lower limit and set the upper limit to 1
julia> ylim((nothing, 1))
```
