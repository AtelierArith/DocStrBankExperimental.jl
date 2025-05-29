Set the limits for the x-axis.

The x-axis limits can either be passed as individual arguments or as a tuple of (**x_min**, **x_max**). Setting either limit to **nothing** will cause it to be automatically determined based on the data, which is the default behavior.

:param x*min: 	- the x-axis lower limit, or 	- **nothing** to use an automatic lower limit, or 	- a tuple of both x-axis limits :param x*max: 	- the x-axis upper limit, or 	- **nothing** to use an automatic upper limit, or 	- **nothing** if both x-axis limits were passed as first argument :param adjust: whether or not the limits may be adjusted

**Usage examples:**

.. code-block:: julia

```
julia> # Set the x-axis limits to -1 and 1
julia> xlim((-1, 1))
julia> # Reset the x-axis limits to be determined automatically
julia> xlim()
julia> # Reset the x-axis upper limit and set the lower limit to 0
julia> xlim((0, nothing))
julia> # Reset the x-axis lower limit and set the upper limit to 1
julia> xlim((nothing, 1))
```
