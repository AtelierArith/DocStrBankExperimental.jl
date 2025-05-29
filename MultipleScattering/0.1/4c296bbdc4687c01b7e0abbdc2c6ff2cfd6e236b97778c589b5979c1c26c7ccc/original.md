See also: [`DiscreteImpulse`](@ref), [`ContinuousImpulse`](@ref)

Calculates the time response from the frequency response by approximating an inverse Fourier transform. The time signal is assumed to be real and the frequenices ω_vec are assumed to be positive (can include zero) and sorted. The result is convoluted in time ωith the user specified impulse.

We use the Fourier transform convention: F(ω) =  ∫ f(t)*exp(im*ω*t) dt f(t) = (2π)^(-1) * ∫ F(ω)*exp(-im*ω*t) dt

To easily sample any time, the default is not FFT, but a discrete version of the transform above.
