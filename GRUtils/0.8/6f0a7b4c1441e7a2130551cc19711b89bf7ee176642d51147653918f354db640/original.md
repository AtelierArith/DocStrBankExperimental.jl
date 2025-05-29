```
bar(labels, heights; kwargs...)
bar(heights; kwargs...)
```

Draw a bar plot.

If no specific labels are given, the bars are labelled with integer numbers starting from 1.

If `heights` is a matrix, each column is taken as a different set of data, which are represented as bars of different colors. Use the keyword argument `barposition` with the values `"grouped"` (default) or `"stacked"` to control if the bars are positioned side by side or stacked on top of the previous series.

The keyword arguments `barwidth`, `baseline` and `horizontal` can also be used to modify the aspect of the bars, which by default is:

  * `barwidth = 0.8` (80% of the separation between bars).
  * `baseline = 0.0` (bars starting at zero).
  * `horizontal = false` (vertical bars)

The color of the bars is selected automatically, unless a specific hexadecimal RGB color code is given through the keyword argument `color`.

# Examples

```julia
# Create example data (continent population in million people)
continents = ["Africa", "America", "Asia", "Europe", "Oceania"]
population_1960 = [285, 425, 1687, 606, 16]
population_2010 = [1044, 944, 4170, 735, 36]
population_matrix = [population_1960 population_2010]
# Plot with respect to 500 millions of people
barplot(continents, population_matrix, baseline=500)
legend("1960", "2010") # add legend

```
