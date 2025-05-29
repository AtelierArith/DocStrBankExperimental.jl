```
Returns the polarisation averaged theoretical spectrum calculated with the transfer
matrix method. It consiers light hitting the first medium (incidentRI).

    X = theoretical_spectrum(specType, beam, incidentRI, emergentRI)

        specType: type of spectrum to compute, Reflectance() or Transmittance().
        beam: a PlaneWave structure.
        incidentRI: Array containing the index of refraction of the incident material
            for several wavelengths. For instance, RIdb.air(beam.λ).
        emergentRI: Array containing the index of refraction of the emergent material
            for several wavelengths. For instance, RIdb.silicon(beam.λ).
        X: averaged spectrum = beam.p*Xp + (1.0 - beam.p)*Xs
```
