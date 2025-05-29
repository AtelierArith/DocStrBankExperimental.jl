Convenience function for converting an Nx3 array of RGB values in a colour map to an Nx3 array of CIELAB values.  Function can also be used to convert a 3 channel RGB image to a 3 channel CIELAB image

Note it appears that the Colors.convert() function uses a default white point of D65

```
 Usage:  lab = srgb2lab(rgb)

 Argument:    rgb - A N x 3 array of RGB values or a 3 channel RGB image.
 Returns:     lab - A N x 3 array of Lab values of a 3 channel CIELAB image.

```

See also: lab2srgb
