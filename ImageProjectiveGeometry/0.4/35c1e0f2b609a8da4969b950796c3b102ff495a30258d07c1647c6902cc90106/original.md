noble - Noble's variant of the Harris corner detector

```

Usage:                cimg = noble(img, sigma=1)
              (cimg, r, c) = noble(img, sigma=1; args...)

Arguments:   
           img    - Image to be processed.
                    ::Array{T,2} or ::ImageMeta{T,2} 
           sigma  - Standard deviation of Gaussian summation window. 
                    Typical values to use might be 1-3. Default is 1.
Keyword arguments:
          args... - A sequence of keyword arguments for performing non-maximal suppression.
                    These are: (see nonmaxsuppts() for more details)
           radius - Radius of region considered in non-maximal
                    suppression. Typical values to use might
                    be 1-3 pixels. Default (and minimum value) is 1.
           thresh - Threshold, only features with value greater than
                    threshold are returned. Default is 0.
                N - Maximum number of features to return.  In this case the
                    N strongest features with value above 'thresh' are
                    returned. Default is Inf.
         subpixel - If set to true features are localised to subpixel
                    precision. Default is false.
             img  - Optional image data.  If an image is supplied the
                    detected corners are overlayed on this image. This can
                    be useful for parameter tuning. Default is [].

Returns:
           cimg   - Corner strength image.
           r      - Row coordinates of corner points.
           c      - Column coordinates of corner points.
```

If the input is an ImageMeta cimg will be an ImageMeta with property spatialorder set to ["y","x"] so that it is consistent with the coordinates returned in r, c

With none of the optional keyword arguments specified only `cimg` is returned as a raw corner strength image.  You may then want to look at the values within 'cimg' to determine the appropriate threshold value to use.

Noble's variation of the Harris operator avoids the need to set the parameter `k`.  However the Shi-Tomasi measure is probably what you really want.

See also: harris(), shi_tomasi(), hessianfeatures(), nonmaxsuppts(), structuretensor(), derivative5()
