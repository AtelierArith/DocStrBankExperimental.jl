The logarithmic Gabor function in the frequency domain.

```
Usage: v = loggabor(f::Real, fo::Real, sigmaOnf::Real)

Arguments:
            f - Frequency to evaluate the function at.
           fo - Centre frequency of filter.
     sigmaOnf - Ratio of the standard deviation of the Gaussian
                describing the log Gabor filter's transfer function
                in the frequency domain to the filter center frequency.

sigmaOnf = 0.75 gives a filter bandwidth of about 1 octave.
sigmaOnf = 0.55 gives a filter bandwidth of about 2 octaves.

```
