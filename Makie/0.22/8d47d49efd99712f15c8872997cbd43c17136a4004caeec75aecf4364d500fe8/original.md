```
categorical_colors(colormaplike, categories::Integer)
```

Creates categorical colors and tries to match `categories`. Will error if color scheme doesn't contain enough categories. Will drop the n last colors, if request less colors than contained in scheme.
