```
gyrofrequency(B::BField, p::ParticleLike; kw...)
gyrofrequency(B::BField, mass::Mass, q::Charge)
```

Calculate the gyrofrequency (or cyclotron frequency) of a charged particle's circular motion in a magnetic field. The gyrofrequency is the angular frequency of a charged particle's gyromotion around magnetic field lines.

References: 

  * [PlasmaPy Documentation](https://docs.plasmapy.org/en/latest/api/plasmapy.formulary.frequencies.gyrofrequency.html)

# Examples

```jldoctest; filter = r"(\^-1|⁻¹)"
julia> gyrofrequency(0.01u"T", :p)  # proton gyrofrequency
957883.3292211705 rad s⁻¹

julia> uconvert(u"Hz", gyrofrequency(0.1u"T", :e), Periodic())  # electron gyrofrequency as frequency
2.799248987233304e9 Hz

julia> gyrofrequency(250u"Gauss", "Fe"; z=13)  # Fe2+ ion gyrofrequency
560682.3520611608 rad s⁻¹
```
