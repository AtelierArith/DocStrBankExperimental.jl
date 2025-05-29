```
capture_still(id::Integer)
```

Captures a still image. You have to set gain, exposure etc. beforehand using set*control*value(...).

# Returns:

```
An array containing the image.
```

# Throws:

```
ASIWrapperError if the image format is not supported by the wrapper, or
ASIError in other unfortunate cases
```
