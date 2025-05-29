fitplanedemo - Demonstrates RANSAC plane fitting

Function generates a noisy set of data points with outliers and uses RANSAC to fit a plane.

```
Usage: fitplanedemo(outliers, sigma, t, feedback)

Arguments:
              outliers - Fraction specifying how many points are to be
                         outliers.
              sigma    - Standard deviation of inlying points from the
                         true plane.
              t        - Distance threshold to be used by the RANSAC
                         algorithm for deciding whether a point is an
                         inlier. 
              feedback - Optional flag 0 or 1 to turn on RANSAC feedback
                         information.

Try using:  fitplanedemo(0.3, 0.02, 0.05)
```

See also: ransacfitplane(), fitplane()
