derivative7 - 7-Tap 1st and 2nd discrete derivatives

This function computes 1st and 2nd derivatives of an image using the 7-tap coefficients given by Farid and Simoncelli.  The results are significantly more accurate than simple gradient functions on edges that are at angles other than vertical or horizontal. This, in turn, improves gradient orientation estimation enormously.

```
Usage:  (gx, gy, gxx, gyy, gxy) = derivative7(img, derivative specifiers)

Arguments:
                      im - Image to compute derivatives from. ::Array{T,2}
   derivative specifiers - A tuple of character strings
                           that can be any of "x", "y", "xx", "yy" or "xy"
                           These can be in any order, the order of the
                           computed output arguments will match the order
                           of the derivative specifier strings.
Returns:
 Function returns requested derivatives which can be:
    gx, gy   - 1st derivative in x and y
    gxx, gyy - 2nd derivative in x and y
    gxy      - 1st derivative in y of 1st derivative in x

 Examples:
   Just compute 1st derivatives in x and y
   (gx, gy) = derivative7(img, ("x", "y"))

   Compute 2nd derivative in x, 1st derivative in y and 2nd derivative in y
   (gxx, gy, gyy) = derivative7(img, ("xx", "y", "yy"))
```

See also: derivative5()
