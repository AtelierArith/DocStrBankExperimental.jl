Set current subplot index.

By default, the current plot will cover the whole window. To display more than one plot, the window can be split into a number of rows and columns, with the current plot covering one or more cells in the resulting grid.

Subplot indices are one-based and start at the upper left corner, with a new row starting after every **num_columns** subplots.

:param num*rows: the number of subplot rows :param num*columns: the number of subplot columns :param subplot_indices: 	- the subplot index to be used by the current plot 	- a pair of subplot indices, setting which subplots should be covered 	  by the current plot

**Usage examples:**

.. code-block:: julia

```
julia> # Set the current plot to the second subplot in a 2x3 grid
julia> subplot(2, 3, 2)
julia> # Set the current plot to cover the first two rows of a 4x2 grid
julia> subplot(4, 2, (1, 4))
julia> # Use the full window for the current plot
julia> subplot(1, 1, 1)
```
