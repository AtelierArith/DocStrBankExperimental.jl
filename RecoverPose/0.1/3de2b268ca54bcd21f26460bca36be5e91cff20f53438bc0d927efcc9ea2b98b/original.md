RANSAC algorithm used when there are more points than algorithm requires.

# Arguments:

  * `sample_selector`: Function that given set of ids of the size `n_samples`,   returns input for the `kernel` method.
  * `kernel`: Function that calculates candidates from the sampled data.
  * `rank`: Function that evaluates candidates, computed by `kernel`.   It should return `n_inliers, model`, where `model` can be of any type.   And is not used by the ransac itself. It only uses `n_inliers` to select   which model is better.
  * `n_points`: Total number of points in the data.
  * `n_samples`: Number of points, that `kernel` function accepts.   E.g. `five_point_ransac` sets this value to `5`.
  * `iterations`: Maximum number of iterations to attempt. Default is `100`.
  * `confidence`: Confidence in `[0, 1]` range. The higher the value, the more   certain algorithm is that the picked model does not contain outliers.   Number of iterations performed by RANSAC depends on this value as well.

# Returns:

Number of inliers and the selected model in the format returned by `kernel`.
