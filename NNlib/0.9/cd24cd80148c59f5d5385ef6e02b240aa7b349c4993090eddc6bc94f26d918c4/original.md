```
hann_window(
    window_length::Int, ::Type{T} = Float32; periodic::Bool = true,
) where T <: Real
```

Hann window function (ref: [Window function § Hann and Hamming windows - Wikipedia](https://en.wikipedia.org/wiki/Window_function#Hann_and_Hamming_windows)).

$w[n] = \frac{1}{2}[1 - \cos(\frac{2 \pi n}{N - 1})]$

Where $N$ is the window length.

```julia-repl
julia> lineplot(hann_window(100); width=30, height=10)
     ┌──────────────────────────────┐
   1 │⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⣠⠚⠉⠉⠉⠢⡀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀│
     │⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⡔⠁⠀⠀⠀⠀⠀⠘⢄⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀│
     │⠀⠀⠀⠀⠀⠀⠀⠀⠀⢀⠞⠀⠀⠀⠀⠀⠀⠀⠀⠈⢆⠀⠀⠀⠀⠀⠀⠀⠀⠀│
     │⠀⠀⠀⠀⠀⠀⠀⠀⢀⡎⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠈⢣⠀⠀⠀⠀⠀⠀⠀⠀│
     │⠀⠀⠀⠀⠀⠀⠀⠀⡎⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠈⢦⠀⠀⠀⠀⠀⠀⠀│
     │⠀⠀⠀⠀⠀⠀⢀⠞⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠈⢆⠀⠀⠀⠀⠀⠀│
     │⠀⠀⠀⠀⠀⢀⡜⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠈⢇⠀⠀⠀⠀⠀│
     │⠀⠀⠀⠀⢀⠎⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠈⢦⠀⠀⠀⠀│
     │⠀⠀⠀⢠⠊⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠣⡀⠀⠀│
   0 │⣀⣀⠔⠁⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠙⢤⣀│
     └──────────────────────────────┘
     ⠀0⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀100⠀
```

# Arguments:

  * `window_length::Int`: Size of the window.
  * `::Type{T}`: Elemet type of the window.

# Keyword Arguments:

  * `periodic::Bool`: If `true` (default), returns a window to be used as   periodic function. If `false`, return a symmetric window.

    Following always holds:

```jldoctest
julia> N = 256;

julia> hann_window(N; periodic=true) ≈ hann_window(N + 1; periodic=false)[1:end - 1]
true

julia> hann_window(N) ≈ hamming_window(N; α=0.5f0, β=0.5f0)
true
```

# Returns:

Vector of length `window_length` and eltype `T`.
