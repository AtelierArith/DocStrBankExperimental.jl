```
analysis(x::Vector, w::Vector, L=0, N=length(w)) -> Matrix
analysis(x::Array{Vector}, w::Vector, L=0, N=length(w)) -> Array{Matrix}

stft(x::Vector, w::Vector, L=0, N=length(w)) -> Matrix
stft(x::Array{Vector}, w::Vector, L=0, N=length(w)) -> Array{Matrix}
```

Analyse discrete time-domain signal $\mathrm{x}[n]$ using Short-Time Fourier Transform given by

$$
\mathrm{X}[sH, \omega] =
    \sum_{n = -\infty}^{+\infty}
        \mathrm{w}[n - sH] \ \mathrm{x}[n] e^{-j\omega n},
$$

where $s$ and $\omega$ denotes segment index and angular frequency respectively, $\mathrm{w}[n]$ is a discrete time-domain signal of analysis window, and $H$ is nonnegative integer value that determine number of samples between two consecutive signal segments (also known as `hop`).

# Parameters

  * `x` - An array containing samples of a discrete time-domain signal.
  * `w` - An array containing samples of a discrete time-domain analysis window.
  * `L` - An overlap in samples between two consecutive segments.       Default value is `0`.
  * `N` - A number of discrete frequency bins to be used in the DFT computation.       Default value is `length(w)`.       If `N < length(w)`, then `N=length(w)` is enforced to avoid loss of       information.

# Returns

  * `X` - A complex matrix containing STFT-domain signal.

# Note

1. Relation between $H$ and $L$ is given as $H = W - L$ where $W$ is a length of a window.
2. For real-valued (`x isa Real`) input signals function returns matrix is of size `(N÷2+1, S)` where `S` is a number of segments; i.e., one-sided spectrum.
3. For complex-valued (`x isa Complex`) input signals function returns matrix is of size `(N, S)` where `S` is a number of segments; i.e., two-sided spectrum.

# Examples

```julia
import STFT

x = rand(10000) # Generate mock signal
W = 64          # Window length
w = ones(W)     # Rectangular analysis window
H = 10          # Hop
L = W - H       # Overlap

X = STFT.analysis(x, w, L)  # Analysis
```

```julia
using STFT

x = rand(100)   # Generate mock signal
W = 64          # Window length
w = ones(W)     # Rectangular analysis window
H = 4           # Hop
L = W - H       # Overlap

X  = stft(x, w, L)  # Analysis
```
