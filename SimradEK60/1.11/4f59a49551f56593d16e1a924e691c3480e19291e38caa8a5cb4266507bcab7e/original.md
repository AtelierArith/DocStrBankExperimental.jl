```
Sv(Pr, λ, G, Ψ, c, α, Pt, τ, Sa, R)
```

where:

R = the corrected range (m) - see TVG Range Correction

Pr = received power (dB re 1 W) - see Simrad EK numbers to Power

Pt = transmitted power (W)

α = absorption coefficient (dB/m)

G0 = transducer peak gain (non-dimensional) calculated as 10^(G/10)

G is the Transducer gain (dB re 1)

λ = wavelength (m) = c/f

f = frequency (Hz)

c = sound speed (m/s)

τ = transmit pulse duration (s) - also known as the TransmittedPulseLength

ψ = Equivalent Two-way beam angle (Steradians) calculated as 10^(Ψ/10)

Ψ is the Two-way beam angle (dB re 1 Steradian)

Sa = Simrad correction factor (dB re 1m−1) determined during calibration. This represents the correction required to the Sv constant to harmonize the TS and NASC measurements.
