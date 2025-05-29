```
clearplot([plotobj::DisplazWindow=current()], [pattern1, ...])
```

Clear all or a subset of datasets in a plot window.

If not specified, `plotobj` is the current plot window.  If no patterns are supplied, clears all data sets.  If one or more patterns are given, the dataset labels matching those patterns will be removed.  Patterns shoudl be specified using unix shell glob pattern syntax.
