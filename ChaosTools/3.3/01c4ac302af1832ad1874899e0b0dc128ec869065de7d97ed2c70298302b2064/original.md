```
yin(sig::Vector, sr::Int; kwargs...) -> F0s, frame_times
```

Estimate the fundamental frequency (F0) of the signal `sig` using the YIN algorithm [^1]. The signal `sig` is a vector of points uniformly sampled at a rate `sr`.

## Keyword arguments

  * `w_len`: size of the analysis window [samples == number of points]
  * `f_step`: size of the lag between two consecutive frames [samples == number of points]
  * `f0_min`: Minimum fundamental frequency that can be detected [linear frequency]
  * `f0_max`: Maximum fundamental frequency that can be detected [linear frequency]
  * `harmonic_threshold`: Threshold of detection. The algorithm returns the first minimum of the CMNDF function below this threshold.
  * `diffference_function`: The difference function to be used (by default `ChaosTools.difference_function_original`).

## Description

The YIN algorithm [^CheveigneYIN2002] estimates the signal's fundamental frequency `F0` by basically looking for the period `τ0`  which minimizes the signal's autocorrelation. This autocorrelation is calculated for signal segments (frames), composed of two windows of length `w_len`. Each window is separated by a distance `τ`, and the idea is that the distance which minimizes the pairwise difference between each window is considered to be the fundamental period `τ0` of that frame.

More precisely, the algorithm first computes the cumulative mean normalized difference function (MNDF) between two windows of a frame for several candidate periods `τ` ranging from `τ_min=sr/f0_max` to `τ_max=sr/f0_min`. The MNDF is defined as

$$
d_t^\prime(\tau) = \begin{cases}
        1 & \text{if} ~ \tau=0 \\
        d_t(\tau)/\left[{(\frac 1 \tau) \sum_{j=1}^{\tau} d_{t}(j)}\right] & \text{otherwise}
        \end{cases}
$$

where `d_t` is the difference function:

$$
d_t(\tau) = \sum_{j=1}^W (x_j - x_{j+\tau})^2
$$

It then refines the local minima of the MNDF using parabolic (quadratic) interpolation. This is done by taking each minima, along with their first neighbor points, and finding the minimum of the corresponding interpolated parabola. The MNDF minima are substituted by the interpolation minima. Finally, the algorithm chooses the minimum with the smallest period and with a corresponding MNDF below the `harmonic threshold`. If this doesn't exist, it chooses the period corresponding to the global minimum. It repeats this for frames starting at the first signal point, and separated by a distance `f_step` (frames can overlap), and returns the vector of frequencies `F0=sr/τ0` for each frame, along with the start times of each frame.

As a note, the physical unit of the frequency is 1/[time], where [time] is decided by the sampling rate `sr`. If, for instance, the sampling rate is over seconds, then the frequency is in Hertz.

[^CheveigneYIN2002]: De Cheveigné, A., & Kawahara, H. (2002). YIN, a fundamental frequency estimator for

speech and music. The Journal of the Acoustical Society of America, 111(4), 1917-1930.
