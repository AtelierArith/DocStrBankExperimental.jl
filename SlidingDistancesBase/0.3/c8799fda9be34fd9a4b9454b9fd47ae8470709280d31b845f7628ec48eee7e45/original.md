```julia
sliding_pca(
    X;
    fs,
    w,
    cutoff_freq,
    pad,
    normalize_win,
    center
)

```

Sliding-window PCA. Returns `U1 ∈ 𝐑(N)` the main principal-component loading scaled with the singular value, and `V1 ∈ 𝐑(d × N)` the main principal direction.

# Arguments:

  * `X`: Signal ∈ 𝐑(d × N)
  * `fs`: Sampling frequency
  * `w`: Window length in seconds
  * `cutoff_freq`: Frequencies below this will be removed. Set to 0 to avoid filtering.
  * `pad`: if true, the return value will be padded with zeros to account for the fact that the analysis uses sliding windows and produce a slightly shorter output. If `pad = true`, the output will have the same length as the input.
  * `normalize_win`: remove the mean from each window before calculating svd.
  * `center`: Index into `X` at the center of the window (default) or at a position in the window proportional to how far along in the signal the window is taken.
