FFTOp(T::Type, shape::Tuple, shift=true, unitary=true)

returns an operator which performs an FFT on Arrays of type T

# Arguments:

  * `T::Type`       - type of the array to transform
  * `shape::Tuple`  - size of the array to transform
  * (`shift=true`)  - if true, fftshifts are performed
  * (`unitary=true`)  - if true, FFT is normalized such that it is unitary
