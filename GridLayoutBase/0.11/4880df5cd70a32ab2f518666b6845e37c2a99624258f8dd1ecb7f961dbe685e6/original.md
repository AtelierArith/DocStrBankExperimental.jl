```
tight_bbox(gl::GridLayout)
```

Compute the boundingbox that would be the fitting `suggestedbbox` for the current contents of the `GridLayout`. If a `GridLayout` contains fixed-size content or aspect-constrained columns, for example, it is likely that the solved size of the `GridLayout` differs from its `suggestedbbox`. With the result of `tight_bbox` the `suggestedbbox` can be adjusted (for example by resizing a figure), so that all content fits the available space. The size includes possible padding, such as from an `Outside` alignmode on the `GridLayout`.
