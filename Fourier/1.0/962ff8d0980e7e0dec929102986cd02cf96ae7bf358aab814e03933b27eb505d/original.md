```
imdft(ary, samples[, shift, Q])
```

Compute and return the 2D inverse DFT via a matrix triple product. Equivalent to fftshift(ifft(ifftshift(ary))) if shift==0, samples=size(ary), Q=1.

samples is the number of samples in the output domain.  If it is an integer, it is broadcast to both dimensions.  Otherwise it may be a tuple to provide each.

shift is used to move the origin.  If the output grid with shift=0 spanned -10:1:9 Hz, shift=10 will move the output grid to 0:1:19Hz.  The unit is samples, not hertz.  The first argument is along x, or the columns of the matrix, not dim 0.

Q controls the oversampling factor.  It is equivalent to zero padding the input array by the same factor.  E.g. mdft of a 256x256 array with Q=2 is the same as zero padding it to 512x512 and FFTing that.

See also: [`mdft`](@ref)

# References

"Fast computation of Lyot-style coronagraph propagation" Soummer et al, oe-15-24-15935
