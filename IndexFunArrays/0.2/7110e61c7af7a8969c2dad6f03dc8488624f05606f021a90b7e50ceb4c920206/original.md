```
Ctr
```

Abstract type to specify the reference position from which several other types subtype.

# Possible subtypes

  * `CtrCorner`: Set the reference pixel in the corner
  * `CtrFFT`: Set the reference pixel to the FFT center.
  * `CtrFT`: Set the reference pixel to the FT center. FT means that the zero frequency is at the FFT convention center (`size ÷ 2 + 1`).
  * `CtrRFFT`: Set the reference pixel to the RFFT center. Same as `CtrFFT` but the first dimension has center at 1.
  * `CtrRFT`: Set the reference pixel to the RFT center. FT means that the zero frequency is at the FFT convention center (`size ÷ 2 + 1`).            Same as `CtrFT` but the first dimension has center at 1.
  * `CtrMid`: Set the reference pixel to real mid. For uneven arrays it is the center pixel, for even arrays it is the centered around a half pixel.
  * `CtrEnd` Set the reference to the end corner (last pixel)
