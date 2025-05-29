ransac - Robustly fits a model to data with the RANSAC algorithm

```
Usage:

(M, inliers) = ransac(x, fittingfn, distfn, degenfn s, t, feedback,
                      maxDataTrials, maxTrials)

Arguments:
    x         - Data sets to which we are seeking to fit a model M
                It is assumed that x is of size [d x Npts]
                where d is the dimensionality of the data and Npts is
                the number of data points.

    fittingfn - Reference to a function that fits a model to s
                data from x.  It is assumed that the function is of the
                form:
                   M = fittingfn(x)
                Note it is possible that the fitting function can return
                multiple models (for example up to 3 fundamental matrices
                can be fitted to 7 pairs of matched points).  In this
                case it is assumed that the fitting function returns an
                array of models.
                If this function cannot fit a model it should return M as
                an empty matrix.

    distfn    - Reference to a function that evaluates the
                distances from the model to data x.
                It is assumed that the function is of the form:
                   (inliers, M) = distfn(M, x, t)
                This function must evaluate the distances between points
                and the model returning the indices of elements in x that
                are inliers, that is, the points that are within distance
                't' of the model.  Additionally, if M is an array of
                possible models distfn() will return the model that has the
                most inliers.  If there is only one model this function
                must still copy the model to the output.  After this call M
                will be a single object representing only one model.

    degenfn   - Reference to a function that determines whether a
                set of datapoints will produce a degenerate model.
                This is used to discard random samples that do not
                result in useful models.
                It is assumed that degenfn is a boolean function of
                the form:
                   r = degenfn(x)
                It may be that you cannot devise a test for degeneracy in
                which case you should write a dummy function that always
                returns a value of true and rely on fittingfn() to return
                an empty model should the data set be degenerate.

    s         - The minimum number of samples from x required by
                fittingfn to fit a model.

    t         - The distance threshold between a data point and the model
                used to decide whether the point is an inlier or not.

    feedback  - An optional boolean flag. If set to true the trial count and the
                estimated total number of trials required is printed out at
                each step.  Defaults to false.

maxDataTrials - Maximum number of attempts to select a non-degenerate
                data set. This parameter is optional and defaults to 100.

    maxTrials - Maximum number of iterations. This parameter is optional and
                defaults to 1000.

    p         - Desired probability of choosing at least one sample
                free from outliers, defaults to 0.99

Returns:
    M         - The model having the greatest number of inliers.
    inliers   - An array of indices of the elements of x that were
                the inliers for the best model.
```

For an example of the use of this function see ransacfithomography() or ransacfitplane()
