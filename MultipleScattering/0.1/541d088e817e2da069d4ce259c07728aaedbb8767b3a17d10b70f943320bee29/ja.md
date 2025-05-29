```jldoctest
julia> using FFTW

julia> function time_to_frequency(time_result::TimeSimulationResult)
           # Assuming time_result has a field `signal` which is a real-valued time signal
           N = length(time_result.signal)
           freq_signal = fft(time_result.signal) / N
           # Only take the positive frequencies
           positive_freqs = freq_signal[1:div(N+1, 2)]
           return FrequencySimulationResult(positive_freqs)
       end
```
