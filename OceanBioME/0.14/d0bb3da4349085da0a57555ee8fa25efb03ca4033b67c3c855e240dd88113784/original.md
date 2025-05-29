```
Biogeochemistry(underlying_biogeochemistry;
                light_attenuation = nothing,
                sediment = nothing,
                particles = nothing,
                modifiers = nothing)
```

Construct a biogeochemical model based on `underlying_biogeochemistry` which may have a `light_attenuation` model, `sediment`, `particles`, and `modifiers`.

# Keyword Arguments

  * `light_attenuation_model`: light attenuation model which integrated the attenuation of available light
  * `sediment_model`: slot for `AbstractSediment`
  * `particles`: slot for `BiogeochemicalParticles`
  * `modifiers`: slot for components which modify the biogeochemistry when the tendencies have been calculated or when the state is updated
