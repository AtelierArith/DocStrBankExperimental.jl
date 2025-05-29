```
generate_stimulus(s::Stimgen)
```

Generate one stimulus sound.

Returns waveform, sample rate, spectral representation,  binned representation, and a frequency vector  (the last two empty if s >: BinnedStimgen).  Methods are specialized for each concrete subtype of Stimgen.
