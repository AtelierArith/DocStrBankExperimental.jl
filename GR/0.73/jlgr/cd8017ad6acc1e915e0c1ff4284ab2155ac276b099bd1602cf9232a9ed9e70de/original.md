Set the intervals of the ticks for the X, Y or Z axis.

Use the function `xticks`, `yticks` or `zticks` for the corresponding axis.

:param minor: the interval between minor ticks. :param major: (optional) the number of minor ticks between major ticks.

**Usage examples:**

.. code-block:: julia

```
julia> # Minor ticks every 0.2 units in the X axis
julia> xticks(0.2)
julia> # Major ticks every 1 unit (5 minor ticks) in the Y axis
julia> yticks(0.2, 5)
```
