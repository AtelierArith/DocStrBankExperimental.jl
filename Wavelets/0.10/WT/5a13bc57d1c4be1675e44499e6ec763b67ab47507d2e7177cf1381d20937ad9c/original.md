```
wavelet(c[, t=WT.Filter][, boundary=WT.Periodic][, s=Real])
```

Construct wavelet type where `c` is a wavelet class, `t` is the transformation type (`WT.Filter` or `WT.Lifting`), and `boundary` is the type of boundary treatment. In the continuous case, s>0 is the number of wavelets between the octaves $2^J$ and $2^{J+1}$ (defaults to 8, which is most appropriate for music and other audio).

# Examples

```julia
wavelet(WT.coif6)
wavelet(WT.db1, WT.Lifting)
wavelet(WT.morl,4)
```

**See also:** `WT.WaveletClass`
