```
allocate_buffer(width::Integer, height::Integer, img_type::ASI_IMG_TYPE)
```

Allocates an image buffer for the camera to write to.

# Args:

```
width: Image width
height: Image height
img_type: One of
    -ASI_IMG_RAW8
    -ASI_IMG_Y8
    -ASI_IMG_RAW16
    -ASI_IMG_RAW24
```

# Returns:

```
A zero-initialized array of the appropriate shape.
```

# Throws:

```
ASIWrapperError if an unsupported image type is given.
```
