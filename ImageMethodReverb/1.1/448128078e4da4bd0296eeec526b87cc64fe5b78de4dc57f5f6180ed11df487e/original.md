`h, seed = rim(xs, xr, L, T60, Nt, Fs)`

Computes a synthetic acoustic room impulse response (RIR).

#### Arguments:

  * `xs`  : source position (m)
  * `xr`  : microphone position (m)
  * `L`   : room dimensions (m)
  * `beta`/`T60` : 6 element containing reflection coefficients of walls/reverberation time
  * `Nt`  : length of the RIR (samples)
  * `Fs`  : sampling frequency (Hz)

#### Keyword Arguments:

  * `c = 343`    : speed of sound (m/s)
  * `Rd = 1e-1`  : random displacement (m)
  * `N = (0,0,0)`: 3 element representing order of reflection when `N == (0,0,0)` full order is computed.
  * `Tw = 20`    : taps of fractional delay filter (samples)
  * `Fc = 0.9`   : cut-off frequency of fractional delay filter (samples)
  * `T=Float64`  : data type

#### Outputs:

  * `h`: vector or matrix where each column is an impulse response or the sound pressure if `s` was specified corresponding to the microphone positions `xr`
  * `seed`: randomization seed to preserve spatial properties when other RIR at different position are needed
