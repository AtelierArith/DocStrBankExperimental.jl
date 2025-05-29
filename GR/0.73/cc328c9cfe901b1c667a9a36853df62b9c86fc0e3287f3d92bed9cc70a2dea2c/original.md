```
setcharexpan(factor::Real)
```

Set the current character expansion factor (width to height ratio).

**Parameters:**

`factor` :     Text expansion factor applied to the nominal text width-to-height ratio

`setcharexpan` defines the width of subsequent text output primitives. The expansion factor alters the width of the generated characters, but not their height. The default text expansion factor is 1, or one times the normal width-to-height ratio of the text.
