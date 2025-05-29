```
resize_to_layout!(fig::Figure)
```

Resize `fig` so that it fits the current contents of its top `GridLayout`. If a `GridLayout` contains fixed-size content or aspect-constrained columns, for example, it is likely that the solved size of the `GridLayout` differs from the size of the `Figure`. This can result in superfluous whitespace at the borders, or content clipping at the figure edges. Once resized, all content should fit the available space, including the `Figure`'s outer padding.
