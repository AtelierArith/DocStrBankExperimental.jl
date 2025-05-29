derivative3 - 3-Tap discrete derivative filters

This function computes 1st derivatives of an image using the 3-tap coefficients given by Farid and Simoncelli.  The results are significantly more accurate than simple gradient functions on edges that are at angles other than vertical or horizontal. This, in turn, improves gradient orientation estimation enormously.  If you are after extreme accuracy try using derivative7().

```
Usage:  (gx, gy) = derivative3(img, derivative specifiers)

Arguments:
                     img - Image to compute derivatives from. ::Array{T,2}
   derivative specifiers - A tuple of character strings
                           that can be any of "x" or "y"
                           These can be in any order, the order of the
                           computed output arguments will match the order
                           of the derivative specifier strings.
Returns:
 Function returns requested derivatives which can be:
    gx, gy   - 1st derivative in x and y

 Example:
   Compute 1st derivatives in x and y
   (gx, gy) = derivative3(img, ("x", "y"))
```

See also: derivative5(), derivative7()
