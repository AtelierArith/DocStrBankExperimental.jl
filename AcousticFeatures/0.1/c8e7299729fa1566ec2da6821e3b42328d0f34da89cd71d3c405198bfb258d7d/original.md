Operator for computing the power spectrum

# Constructor

```
PowerSpec(;
          fs       :: Int = 16000,          # sampling frequency
          fmin     :: Real = 0,             # min frequency
          fmax     :: Real = fs/2,          # max frequency
          winlen   :: Int = 256,            # window length
          dilation :: Int = 1,              # down-sample ratio
          stride   :: Int = winlen/2,       # distance between two adjacent frames
          nffts    :: Int = winlen,         # the bins of FFT transform
          donorm   :: Bool = false,         # whether normalize the spectrum
          winfunc  :: Function = hanning,   # the windowing function
          type     :: DataType = Vector{Float32})
```

where [`fmin`, `fmax`] is the frequency region of interest, `type` is the input's type (Matrix or Vector).  If the `donorm` is true, then the elements of window would be divided by the sqrt of window energy.
