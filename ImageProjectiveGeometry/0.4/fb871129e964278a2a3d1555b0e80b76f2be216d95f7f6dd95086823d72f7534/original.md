coherence - Compute image coherence from structure tensor

```
Usage:      cimg = coherence(img, sigma=1)

Arguments:   
           img    - Image to be processed.
                    ::Array{T,2} or ::ImageMeta{T,2} 
           sigma  - Standard deviation of Gaussian summation window. 
                    Typical values to use might be 1-3. Default is 1.
Returns:
           cimg   - Coherence image.
```

Coherence is defined as the difference between the eigenvalues of the structure tensor divided by the sum of the eigenvalues, all squared.  

```
     ((L1-L2)./(L1+L2)).^2
```

A small value indicates that the eigenvalues are similar in magnitude and hence the local structure has a strong 2D component.

If the input is an ImageMeta cimg will be an ImageMeta with property spatialorder set to ["y","x"].

See also: structuretensor()
