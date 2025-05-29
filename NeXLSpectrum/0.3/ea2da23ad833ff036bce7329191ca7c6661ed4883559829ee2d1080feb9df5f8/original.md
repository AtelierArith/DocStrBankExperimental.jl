```
subdivide(spec::Spectrum, n::Int)::Vector{Spectrum}
```

Splits the event data in one spectrum into n spectra by assigning each event to a pseudo-random choice of one of the n result spectra.  Produces n spectra that act as though the original spectrum was collected in n time intervals of LiveTime/n.  This is quite slow because it needs to call rand() for each count in the spectrum (not just each channel).
