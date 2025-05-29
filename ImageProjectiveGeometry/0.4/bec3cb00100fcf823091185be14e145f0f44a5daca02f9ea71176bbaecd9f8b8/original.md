fitlinedemo - Demonstrates RANSAC line fitting.

Function generates a noisy set of data points with outliers and uses RANSAC to fit a line.

```
Usage: fitlinedemo(outliers, sigma, t, feedback=false)

Arguments:
              outliers - Fraction specifying how many points are to be
                         outliers.
              sigma    - Standard deviation of inlying points from the
                         true line.
              t        - Distance threshold to be used by the RANSAC
                         algorithm for deciding whether a point is an
                         inlier. 
              feedback - Optional Boolean flag turn on RANSAC feedback
                         information.

Try using:  fitlinedemo(0.3, 0.05, 0.05)
```

See also: ransacfitplane(), fitplane()
