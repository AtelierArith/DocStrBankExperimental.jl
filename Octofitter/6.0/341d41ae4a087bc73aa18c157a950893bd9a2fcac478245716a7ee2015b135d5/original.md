```
sonora_photometry_interpolator(:Keck_L′, [metalicity="+0.0"])
```

Given a supported photometric band and [M/H] metalicity (default=solar), return a function of temperature (K) and mass (M_jup) that gives the  absolute magnitude of the planet in that bandpass.

Supported bands: :MKO*Y, :MKO*Z, :MKO*J, :MKO*H, :MKO*K, :MKO*L′, :MKO*M′, :TwoMASS*J, :TwoMASS*H, :TwoMASS*Ks, :Keck*Ks, :Keck*L′, :Keck*Ms, :SDSS*g′, :SDSS*r′, :SDSS*i′, :SDSS*z′, :IRAC*36, :IRAC*45, :IRAC*57, :IRAC*79, :WISE*W1, :WISE*W2, :WISE*W3, :WISE_W4

Supported metalicities: "+0.0", "-0.5", "+0.5"
