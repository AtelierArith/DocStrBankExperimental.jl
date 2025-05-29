matchbycorrelation - Match image feature points by correlation

Function generates putative matches between previously detected feature points in two images by looking for points that are maximally correlated with each other within windows surrounding each point. Only points that correlate most strongly with each other in both directions are returned.

This implements normalised cross correlation in its most basic form. There is no attempt to deal with scale or orientation differences between the images and thus it will only work if the images are not too dissimilar.

This is a simple-minded N^2 comparison.

```
Usage: (m1, m2, p1ind, p2ind, cormat) =
                matchbycorrelation(img1, p1, img2, p2, w, dmax)

Arguments:
      img1, img2 - Images containing points that we wish to match.
        p1, p2   - Coordinates of feature pointed detected in img1 and
                   img2 respectively using a corner detector (say Harris
                   or phasecong3).  p1 and p2 are [2 x npts] arrays though
                   p1 and p2 are not expected to have the same number
                   of points.  The first row of p1 and p2 gives the row
                   coordinate of each feature point, the second row
                   gives the column of each point.
        w        - Window size (in pixels) over which the correlation
                   around each feature point is performed.  This should
                   be an odd number.
        dmax     - (Optional) Maximum search radius for matching
                   points.  Used to improve speed when there is little
                   disparity between images. Even setting it to a generous
                   value of 1/4 of the image size gives a useful
                   speedup. If this parameter is omitted it defaults to Inf.

Returns:
        m1, m2   - Coordinates of points selected from p1 and p2
                   respectively such that (putatively) m1[:,i] matches
                   m2[:,i]. m1 and m2 are [2 x npts] arrays defining the
                   points in each of the images in the form [row;col].
  p1ind, p2ind   - Indices of points in p1 and p2 that form a match.  Thus,
                   m1 = p1[:,p1ind] and m2 = p2[:,p2ind]
        cormat   - Correlation matrix; rows correspond to points in p1,
                   columns correspond to points in p2
```

This function is slow as mud! Needs some attention.
