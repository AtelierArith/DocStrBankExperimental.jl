```
istft(y;
    n_fft::Int, hop_length::Int = n_fft ÷ 4, window = nothing,
    center::Bool = true, normalized::Bool = false,
    return_complex::Bool = false,
    original_length::Union{Nothing, Int} = nothing,
)
```

Inverse Short-time Fourier Transform.

Return the least squares estimation of the original signal

# Arguments:

  * `y`: Input complex array in the `(n_fft, n_frames, B)` shape.   Where `B` is the optional batch dimension.

# Keyword Arguments:

  * `n_fft::Int`: Size of Fourier transform.
  * `hop_length::Int`: Distance between neighboring sliding window frames.
  * `window`: Window function that was applied to the input of `stft`.   If `nothing` (default), then no window was applied.
  * `center::Bool`: Whether input to `stft` was padded on both sides   so that $t$-th frame is centered at time $t \times \text{hop length}$.   Padding is done with `pad_reflect` function.
  * `normalized::Bool`: Whether input to `stft` was normalized.
  * `return_complex::Bool`: Whether the output should be complex,   or if the input should be assumed to derive from a real signal and window.
  * `original_length::Union{Nothing, Int}`: Optional size of the first dimension   of the input to `stft`. Helps restoring the exact `stft` input size.   Otherwise, the array might be a bit shorter.
