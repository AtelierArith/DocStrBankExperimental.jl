undistortimage - Removes lens distortion from an image

```
Usage 1:  nimg = undistortimage(img, f, ppx, ppy, k1, k2, k3, p1, p2)

Arguments:
         img - Image to be corrected.
           f - Focal length in terms of pixel units
               (focal_length_mm/pixel_size_mm)
    ppx, ppy - Principal point location in pixels.
  k1, k2, k3 - Radial lens distortion parameters.
      p1, p2 - Tangential lens distortion parameters.

Usage 2.  nimg = undistortimage(img, camera)

Arguments:
         img - Image to be corrected.
         cam - Camera structure.

Returns:
         nimg - Corrected image.
```

It is assumed that radial and tangential distortion parameters are computed/defined with respect to normalised image coordinates corresponding to an image plane 1 unit from the projection centre.  This is why the focal length is required.
