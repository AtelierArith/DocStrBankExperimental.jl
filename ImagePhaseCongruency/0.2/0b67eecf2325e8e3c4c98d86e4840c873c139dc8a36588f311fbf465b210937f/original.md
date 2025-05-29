2D Fourier transform of Moisan's periodic image component.

```
Usage: (P, S, p, s) = perfft2(img)

Argument: img - Image to be transformed
Returns:    P - 2D fft of periodic image component
            S - 2D fft of smooth component
            p - Periodic component (spatial domain)
            s - Smooth component (spatial domain)
```

Moisan's "Periodic plus Smooth Image Decomposition" decomposes an image into two components

```
    img = p + s
```

where s is the 'smooth' component with mean 0 and p is the 'periodic' component which has no sharp discontinuities when one moves cyclically across the image boundaries.

This decomposition is very useful when one wants to obtain an FFT of an image with minimal artifacts introduced from the boundary discontinuities.  The image p gathers most of the image information but avoids periodization artifacts.

The typical use of this function is to obtain a 'periodic only' fft of an image

```
  P = perfft2(img)
```

Displaying the amplitude spectrum of P will yield a clean spectrum without the typical vertical-horizontal 'cross' arising from the image boundaries that you would normally see.

Note if you are using the function to perform filtering in the frequency domain you may want to retain s (the smooth component in the spatial domain) and add it back to the filtered result at the end.

The computational cost of obtaining the 'periodic only' FFT involves taking an additional FFT.
