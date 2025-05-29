Convenience function for converting an Nx3 array of CIELAB values in a colour map to an Nx3 array of RGB values.  Function can also be used to convert a 3 channel CIELAB image to a 3 channel RGB image

Note it appears that the Colors.convert() function uses a default white point of D65

```
 Usage:  rgb = srgb2lab(lab)

 Argument:   lab - A N x 3 array of CIELAB values of a 3 channel CIELAB image.
 Returns:    rgb - A N x 3 array of RGB values or a 3 channel RGB image.
```

See also: srgb2lab
