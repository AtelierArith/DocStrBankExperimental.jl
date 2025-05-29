normalize - Normalizes image values to 0-1, or to desired mean and variance

```
Usage 1:      nimg = normalize(img)
```

Offsets and rescales image so that the minimum value is 0 and the maximum value is 1.

```
Usage 2:      nimg = normalize(img, reqmean, reqvar)

Arguments:  img     - A grey-level input image.
            reqmean - The required mean value of the image.
            reqvar  - The required variance of the image.
```

Offsets and rescales image so that nimg has mean reqmean and variance reqvar.
