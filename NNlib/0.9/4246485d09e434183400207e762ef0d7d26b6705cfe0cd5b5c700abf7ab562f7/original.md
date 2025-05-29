```
melscale_filterbanks(;
    n_freqs::Int, n_mels::Int, sample_rate::Int,
    fmin::Float32 = 0f0, fmax::Float32 = Float32(sample_rate ÷ 2))
```

Create triangular Mel scale filter banks (ref: [Mel scale - Wikipedia](https://en.wikipedia.org/wiki/Mel_scale)). Each column is a filterbank that highlights its own frequency.

# Arguments:

  * `n_freqs::Int`: Number of frequencies to highlight.
  * `n_mels::Int`: Number of mel filterbanks.
  * `sample_rate::Int`: Sample rate of the audio waveform.
  * `fmin::Float32`: Minimum frequency in Hz.
  * `fmax::Float32`: Maximum frequency in Hz.

# Returns:

Filterbank matrix of shape `(n_freqs, n_mels)` where each column is a filterbank.

```jldoctest
julia> n_mels = 8;

julia> fb = melscale_filterbanks(; n_freqs=200, n_mels, sample_rate=16000);

julia> plot = lineplot(fb[:, 1]);

julia> for i in 2:n_mels
           lineplot!(plot, fb[:, i])
       end

julia> plot
     ┌────────────────────────────────────────┐
   1 │⠀⡀⢸⠀⢸⠀⠀⣧⠀⠀⢸⡄⠀⠀⠀⣷⠀⠀⠀⠀⠀⣷⠀⠀⠀⠀⠀⠀⢀⣿⡀⠀⠀⠀⠀⠀⠀⠀⠀⠀│
     │⠀⡇⢸⡆⢸⡇⠀⣿⠀⠀⡜⡇⠀⠀⢰⠋⡆⠀⠀⠀⢰⠁⡇⠀⠀⠀⠀⠀⡸⠀⢣⠀⠀⠀⠀⠀⠀⠀⠀⠀│
     │⠀⣿⢸⡇⡇⡇⢰⠹⡄⠀⡇⢱⠀⠀⢸⠀⢣⠀⠀⠀⡜⠀⢸⡀⠀⠀⠀⢀⠇⠀⠈⡇⠀⠀⠀⠀⠀⠀⠀⠀│
     │⠀⣿⡇⡇⡇⡇⢸⠀⡇⢀⠇⠸⡀⠀⡇⠀⠸⡀⠀⢀⠇⠀⠀⢇⠀⠀⠀⡸⠀⠀⠀⠸⡄⠀⠀⠀⠀⠀⠀⠀│
     │⢠⢻⡇⡇⡇⢱⢸⠀⢇⢸⠀⠀⡇⢀⠇⠀⠀⡇⠀⢸⠀⠀⠀⠸⡀⠀⢠⠇⠀⠀⠀⠀⢱⠀⠀⠀⠀⠀⠀⠀│
     │⢸⢸⡇⢱⡇⢸⡇⠀⢸⢸⠀⠀⢣⢸⠀⠀⠀⢸⠀⡇⠀⠀⠀⠀⢇⠀⡜⠀⠀⠀⠀⠀⠈⢇⠀⠀⠀⠀⠀⠀│
     │⢸⢸⡇⢸⠀⢸⡇⠀⢸⡇⠀⠀⢸⡎⠀⠀⠀⠈⣶⠁⠀⠀⠀⠀⠸⣤⠃⠀⠀⠀⠀⠀⠀⠘⡆⠀⠀⠀⠀⠀│
     │⢸⠀⡇⢸⠀⠀⡇⠀⠀⡇⠀⠀⠀⡇⠀⠀⠀⠀⣿⠀⠀⠀⠀⠀⠀⣿⠀⠀⠀⠀⠀⠀⠀⠀⢱⡀⠀⠀⠀⠀│
     │⢸⢸⡇⢸⠀⢸⡇⠀⢸⡇⠀⠀⢸⢇⠀⠀⠀⢀⠿⡀⠀⠀⠀⠀⢰⠛⡄⠀⠀⠀⠀⠀⠀⠀⠀⢣⠀⠀⠀⠀│
     │⢸⢸⡇⡸⡇⢸⡇⠀⢸⢸⠀⠀⡜⢸⠀⠀⠀⢸⠀⡇⠀⠀⠀⠀⡎⠀⢣⠀⠀⠀⠀⠀⠀⠀⠀⠘⡆⠀⠀⠀│
     │⢸⢸⡇⡇⡇⡸⢸⠀⡎⢸⠀⠀⡇⠈⡆⠀⠀⡇⠀⢸⠀⠀⠀⢰⠁⠀⠘⡆⠀⠀⠀⠀⠀⠀⠀⠀⠸⡄⠀⠀│
     │⡇⢸⡇⡇⡇⡇⢸⠀⡇⠈⡆⢰⠁⠀⡇⠀⢰⠁⠀⠈⡆⠀⠀⡎⠀⠀⠀⢱⠀⠀⠀⠀⠀⠀⠀⠀⠀⢣⠀⠀│
     │⡇⢸⢸⡇⡇⡇⠸⣰⠃⠀⡇⡸⠀⠀⢸⠀⡜⠀⠀⠀⢣⠀⢸⠁⠀⠀⠀⠈⡆⠀⠀⠀⠀⠀⠀⠀⠀⠈⢇⠀│
     │⡇⡇⢸⠇⢸⡇⠀⣿⠀⠀⢣⡇⠀⠀⠸⣄⠇⠀⠀⠀⠸⡀⡇⠀⠀⠀⠀⠀⢱⠀⠀⠀⠀⠀⠀⠀⠀⠀⠸⡄│
   0 │⣇⣇⣸⣀⣸⣀⣀⣟⣀⣀⣸⣃⣀⣀⣀⣿⣀⣀⣀⣀⣀⣿⣀⣀⣀⣀⣀⣀⣈⣇⣀⣀⣀⣀⣀⣀⣀⣀⣀⣱│
     └────────────────────────────────────────┘
     ⠀0⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀200⠀
```
