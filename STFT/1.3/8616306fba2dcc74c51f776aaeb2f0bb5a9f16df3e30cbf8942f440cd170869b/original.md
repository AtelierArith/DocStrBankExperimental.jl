```
synthesis(X::Matrix, w::Vector, L=0, N=length(w)) -> Vector

istft(X::Matrix, w::Vector, L=0, N=length(w)) -> Vector
```

Syntesise discrete time-domain signal $y[n]$ from STFT-domain signal $Y_w[sH, n]$. An arbitrary STFT-domain signal $Y_w[sH, n]$, in general, is not a valid STFT in the sense that there is no discrete time-domian signal whoes STFT is given by $Y_w[sH, n]$ [1]. As result, time-domain signal must be estimated using following formula [1]:

$$
y[n] = \frac{
    \sum\limits_{s=-\infty}^{+\infty} w[n - sH] \ y_w[sH, n]
}{
    \sum\limits_{s=-\infty}^{+\infty} w^2[n - sH]
},
$$

where $w[n]$ is time-domain signal of analysis window, $y_w[sH, n]$ is time-domain representation of $Y_w[sH, n]$, and $H$ is nonnegative integer value that determine number of samples between two consecutive signal segments (also known as `hop`).

# Parameters

  * `X` - An matrix containing samples of a discrete STFT-domain signal.
  * `w` - An array containing samples of a discrete time-domain analysis window.
  * `L` - An overlap in samples between two consecutive segments.       Default value is `0`.
  * `N` - A number of discrete frequency bins to be used in the inverse DFT       computation. Default value is `length(w)`.       If `N < length(w)`, then `N=length(w)` is enforced to avoid loss of       information.

# Returns

  * `x` - A real-valued vector containing estimated time-domain signal.

# Note

1. Relation between $H$ and $L$ is given as $H = W - L$ where $W$ is a length of a window.
2. This function supports only synthesis of real-valued signals from one-sided STFT-domain signal.
3. Synthesised time-domain signal might be shorter than analysed one, since only whole segments are analysed.

# Example

```julia
import STFT

x = rand(100)   # Generate mock signal
W = 64          # Window length
w = ones(W)     # Rectangular analysis window
H = 4           # Hop
L = W - H       # Overlap

X  = STFT.analysis(x, w, L)  # Analysis
xr = STFT.synthesis(X, w, L) # Synthesis
```

```julia
using STFT

x = rand(100)   # Generate mock signal
W = 64          # Window length
w = ones(W)     # Rectangular analysis window
H = 4           # Hop
L = W - H       # Overlap

X  = stft(x, w, L)  # Analysis
xr = istft(X, w, L) # Synthesis
```

# References

1. D. Griffin and J. Lim, “Signal estimation from modified short-time Fourier transform,” IEEE Transactions on Acoustics, Speech, and Signal Processing, vol. 32, no. 2, pp. 236–243, Apr. 1984, doi: 10.1109/TASSP.1984.1164317. [[IEEE Xplore](https://ieeexplore.ieee.org/abstract/document/1164317)]
