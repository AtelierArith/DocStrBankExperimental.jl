```
stft(x;
    n_fft::Int, hop_length::Int = n_fft ÷ 4, window = nothing,
    center::Bool = true, normalized::Bool = false,
)
```

Short-time Fourier transform (STFT).

The STFT computes the Fourier transform of short overlapping windows of the input, giving frequency components of the signal as they change over time.

$Y[\omega, m] = \sum_{k = 0}^{N - 1} \text{window}[k] \text{input}[m \times \text{hop length} + k] \exp(-j \frac{2 \pi \omega k}{\text{n fft}})$

where $N$ is the window length, $\omega$ is the frequency $0 \le \omega < \text{n fft}$ and $m$ is the index of the sliding window.

# Arguments:

  * `x`: Input, must be either a 1D time sequence (`(L,)` shape)   or a 2D batch of time sequence (`(L, B)` shape).

# Keyword Arguments:

  * `n_fft::Int`: Size of Fourier transform.
  * `hop_length::Int`: Distance between neighboring sliding window frames.
  * `window`: Optional window function to apply.   Must be 1D vector `0 < length(window) ≤ n_fft`.   If window is shorter than `n_fft`, it is padded with zeros on both sides.   If `nothing` (default), then no window is applied.
  * `center::Bool`: Whether to pad input on both sides so that $t$-th frame   is centered at time $t \times \text{hop length}$.   Padding is done with `pad_reflect` function.
  * `normalized::Bool`: Whether to return normalized STFT,   i.e. multiplied with $\text{n fft}^{-0.5}$.

# Returns:

Complex array of shape `(n_fft, n_frames, B)`, where `B` is the optional batch dimension.
