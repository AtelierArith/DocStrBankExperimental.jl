Draw a bar plot.

If no specific labels are given, the axis is labelled with integer numbers starting from 1.

Use the keyword arguments **barwidth**, **baseline** or **horizontal** to modify the default width of the bars (by default 0.8 times the separation between bars), the baseline value (by default zero), or the direction of the bars (by default vertical).

:param labels: the labels of the bars :param heights: the heights of the bars

**Usage examples:**

.. code-block:: julia

```
julia> # World population by continents (millions)
julia> population = Dict("Africa" => 1216,
                         "America" => 1002,
                         "Asia" => 4436,
                         "Europe" => 739,
                         "Oceania" => 38)
julia> barplot(keys(population), values(population))
julia> # Horizontal bar plot
julia> barplot(keys(population), values(population), horizontal=true)
```
