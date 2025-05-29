```
shannon_entropy(spec::Spectrum)
```

Computes a measure of the information content in a spectrum.  As there become more and more distinct values in a spectrum, this value approaches log2(nchannels(spec)).  This number reflects the number of bits necessary to encode the spectrum data with maximum efficiency.

This is inspired by John Colby's FLAME software which did something similar.  Although, to be honest, I don't know how his algorithm was implemented.
