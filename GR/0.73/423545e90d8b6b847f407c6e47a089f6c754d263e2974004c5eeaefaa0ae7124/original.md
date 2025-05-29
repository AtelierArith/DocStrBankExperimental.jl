```
setscale(options::Int)
```

`setscale` sets the type of transformation to be used for subsequent GR output primitives.

**Parameters:**

`options` :     Scale specification (see Table below)

```
+---------------+--------------------+
|OPTION_X_LOG   |Logarithmic X-axis  |
+---------------+--------------------+
|OPTION_Y_LOG   |Logarithmic Y-axis  |
+---------------+--------------------+
|OPTION_Z_LOG   |Logarithmic Z-axis  |
+---------------+--------------------+
|OPTION_FLIP_X  |Flip X-axis         |
+---------------+--------------------+
|OPTION_FLIP_Y  |Flip Y-axis         |
+---------------+--------------------+
|OPTION_FLIP_Z  |Flip Z-axis         |
+---------------+--------------------+
|OPTION_X_LOG2  |log2 scaled X-axis  |
+---------------+--------------------+
|OPTION_Y_LOG2  |log2 scaled Y-axis  |
+---------------+--------------------+
|OPTION_Z_LOG2  |log2 scaled Z-axis  |
+---------------+--------------------+
|OPTION_X_LN    |ln scaled X-axis    |
+---------------+--------------------+
|OPTION_Y_LN    |ln scaled Y-axis    |
+---------------+--------------------+
|OPTION_Z_LN    |ln scaled Z-axis    |
+---------------+--------------------+
```

`setscale` defines the current transformation according to the given scale specification which may be or'ed together using any of the above options. GR uses these options for all subsequent output primitives until another value is provided. The scale options are used to transform points from an abstract logarithmic or semi-logarithmic coordinate system, which may be flipped along each axis, into the world coordinate system.

Note: When applying a logarithmic transformation to a specific axis, the system assumes that the axes limits are greater than zero.
