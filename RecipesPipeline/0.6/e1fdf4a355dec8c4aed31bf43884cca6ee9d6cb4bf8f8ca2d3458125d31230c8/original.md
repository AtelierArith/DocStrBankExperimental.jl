```
recipe_pipeline!(plt, plotattributes, args)
```

Recursively apply user recipes, type recipes, plot recipes and series recipes to build a list of `Dict`s, each corresponding to a series. At the beginning, `plotattributes` contains only the keyword arguments passed in by the user. Then, add all series to the plot object `plt` and return it.
