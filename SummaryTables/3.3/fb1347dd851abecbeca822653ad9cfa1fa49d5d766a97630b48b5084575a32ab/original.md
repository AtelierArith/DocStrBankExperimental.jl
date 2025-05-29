```
overview_table(table)
```

Creates a `Table` that gives a summarized overview of the columns of `table`, intended to give a quick intuition of the dataset.

To render the graphs with LaTeX, you need to include `\usepackage{tikz}` in your preamble.

## Keyword arguments

  * `max_categories = 10`: Limit the number of categories listed individually for categorical columns, the rest will be lumped together.
  * `label_metadata_key = "label"`: Key to look up column label metadata with.
