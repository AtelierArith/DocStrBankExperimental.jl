# RealFFTs

Highlights of the RealFFTs package:

  * [`RCpair`](@ref): a buffer for in-place real-to-complex and complex-to-real FFTs
  * [`plan_rfft!`](@ref): create a plan for in-place real-to-complex FFTs
  * [`plan_irfft!`](@ref): create a plan for in-place complex-to-real FFTs

Use `real(RC)` and `complex(RC)` to access the real and complex views of the buffer, respectively. `copy!(RC, A)` can be used to copy data (either real- or complex-valued) into the buffer.
