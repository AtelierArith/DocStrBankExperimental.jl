```
imaginary_stability_interval(tab::ODERKTableau;
                             initial_guess = length(tab) - 1)
```

Calculates the length of the imaginary stability interval, i.e., the size of the stability region on the imaginary axis. See also [`stability_region`](@ref).
