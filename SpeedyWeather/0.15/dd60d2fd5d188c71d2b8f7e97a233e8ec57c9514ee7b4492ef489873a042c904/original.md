AquaPlanet sea surface temperatures that are constant in time and longitude, but vary in latitude following a coslat². To be created like

```
ocean = AquaPlanet(spectral_grid, temp_equator=302, temp_poles=273)
```

Fields and options are

  * `temp_equator::Any`: [OPTION] Temperature on the Equator [K]
  * `temp_poles::Any`: [OPTION] Temperature at the poles [K]
