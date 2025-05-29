```
SiteParameters
```

Custom type defining the site parameters of a Fourier spectrum

  * `κ0::T where T<:Real` is the site kappa in units of s
  * `ζ0::U where U<:Real` is the Haendel et al. (2020) ζ parameter (for a reference frequency of $f_0=1$ Hz)
  * `η::V where V<:Real` is the Haendel et al. (2020) η parameter
  * `model::W where W<:SiteAmplification` is a site amplification model defining the impedance function

The argument `model` is currently one of:

  * `SiteAmpUnit` for a generic unit amplification
  * `SiteAmpBoore2016` for the Boore (2016) amplification for $V_{S,30}=760$ m/s
  * `SiteAmpAlAtikAbrahamson2021_ask14_620` for the Al Atik & Abrahamson (2021) inversion of ASK14 for $V_{S,30}=620$ m/s
  * `SiteAmpAlAtikAbrahamson2021_ask14_760` for the Al Atik & Abrahamson (2021) inversion of ASK14 for $V_{S,30}=760$ m/s
  * `SiteAmpAlAtikAbrahamson2021_ask14_1100` for the Al Atik & Abrahamson (2021) inversion of ASK14 for $V_{S,30}=1100$ m/s
  * `SiteAmpAlAtikAbrahamson2021_bssa14_620` for the Al Atik & Abrahamson (2021) inversion of BSSA14 for $V_{S,30}=620$ m/s
  * `SiteAmpAlAtikAbrahamson2021_bssa14_760` for the Al Atik & Abrahamson (2021) inversion of BSSA14 for $V_{S,30}=760$ m/s
  * `SiteAmpAlAtikAbrahamson2021_bssa14_1100` for the Al Atik & Abrahamson (2021) inversion of BSSA14 for $V_{S,30}=1100$ m/s
  * `SiteAmpAlAtikAbrahamson2021_cb14_620` for the Al Atik & Abrahamson (2021) inversion of CB14 for $V_{S,30}=620$ m/s
  * `SiteAmpAlAtikAbrahamson2021_cb14_760` for the Al Atik & Abrahamson (2021) inversion of CB14 for $V_{S,30}=760$ m/s
  * `SiteAmpAlAtikAbrahamson2021_cb14_1100` for the Al Atik & Abrahamson (2021) inversion of CB14 for $V_{S,30}=1100$ m/s
  * `SiteAmpAlAtikAbrahamson2021_cy14_620` for the Al Atik & Abrahamson (2021) inversion of CY14 for $V_{S,30}=620$ m/s
  * `SiteAmpAlAtikAbrahamson2021_cy14_760` for the Al Atik & Abrahamson (2021) inversion of CY14 for $V_{S,30}=760$ m/s
  * `SiteAmpAlAtikAbrahamson2021_cy14_1100` for the Al Atik & Abrahamson (2021) inversion of CY14 for $V_{S,30}=1100$ m/s

See also: [`FourierParameters`](@ref), [`site_amplification`](@ref)
