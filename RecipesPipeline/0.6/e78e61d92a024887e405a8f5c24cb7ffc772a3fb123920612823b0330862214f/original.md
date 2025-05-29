```
process_userrecipe!(plt, attributes_list, attributes)
```

Do plotting package specific post-processing and add series attributes to attributes*list. For example, Plots increases the number of series in `plt`, sets `:series*plotindex` in attributes and possible adds new series attributes for errorbars or smooth.
