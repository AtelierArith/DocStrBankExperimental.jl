```
find_peaks(im; mindist = 10)
```

A primitive peak-finding algorithm. No attempt is made to find all peaks. All pixels with values less than 1/2000 of the maximum are set to zero, then a Niblack binarisation algorithm is applied to produce a peak mask, which is reapplied to the original image and local maxima found. `mindist` specifies the minimum distance in pixels that peaks must be separated in order to be kept. The routine returns fast, slow, max intensity
