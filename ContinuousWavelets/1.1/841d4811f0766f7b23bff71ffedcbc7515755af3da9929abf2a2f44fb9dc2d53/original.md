```
ContWave{Boundary,T}
```

The abstract type encompassing the various types of wavelets implemented in the package. The abstract type has parameters `Boundary<:WaveletBoundary` and `T<:Number`, which gives the element output type. Each has both a constructor, and a default predefined entry. These are:

  * `Morlet`: A complex approximately analytic wavelet that is just a frequency   domain Gaussian with mean subtracted. `Morlet(σ::T) where T<: Real`. `σ`   gives the frequency domain variance of the mother Wavelet. As `σ` goes to   zero, all of the information becomes spatial. Default is `morl` which has   $\sigma=2\pi$.

    $\psi\hat(\omega) \propto \textrm{e}^{-\frac{\sigma^2}{2}}\big(\textrm{e}^{-(\sigma - \omega)^2} -\textrm{e}^{\frac{\omega^2-\sigma^2}{2}}\big)$
  * `Paul{N}`: A complex analytic wavelet, also known as Cauchy wavelets. `pauln` for n in `1:20` e.g. `paul5`

    $\psi\hat(\omega) \propto \chi_{\omega \geq 0} \omega^N\textrm{e}^{-\omega}$
  * `Dog{N}`: Derivative of a Gaussian, where N is the number of   derivatives. `dogn` for `n` in `0:6`. The Sombrero/mexican hat/Marr wavelet   is `n=2`.

    $\psi\hat(\omega) \propto \omega^N\textrm{e}^{-\frac{\omega^2}{2}}$
  * `ContOrtho{OWT}`. OWT is some orthogonal wavelet of type `OrthoWaveletClass`   from [Wavelets.jl](https://github.com/JuliaDSP/Wavelets.jl). This uses an   explicit construction of the mother wavelet for these orthogonal wavelets   to do a continuous transform. Constructed via `ContOrtho(o::W)` where `o`   is from Wavelets.jl. Alternatively, you can get them directly as   `ContOrtho` objects via:

      * `cHaar` Haar Wavelets
      * `cBeyl` Beylkin Wavelets
      * `cVaid` Vaidyanathan Wavelets
      * `cDbn` Daubhechies Wavelets. n ranges from `1:Inf`
      * `cCoifn` Coiflets. n ranges from `2:2:8`
      * `cSymn` Symlets. n ranges from `4:10`
      * `cBattn` Battle-Lemarie wavelets. n ranges from `2:2:6`
