```
Menzel(species; est_prev::Int = 0)
```

The start method `Menzel` implements the algorithm described in Menzel (1997). The method is parameterized for 10 common tree species. It needs previous year's chill days.

The argument `species` is required and must be one of

  * `"Larix decidua"`,
  * `"Picea abies (frueh)"`,
  * `"Picea abies (spaet)"`,
  * `"Picea abies (noerdl.)"`,
  * `"Picea omorika"`,
  * `"Pinus sylvestris"`,
  * `"Betula pubescens"`,
  * `"Quercus robur"`,
  * `"Quercus petraea"`,
  * `"Fagus sylvatica"`.

The optional argument `est_prev` is the integer number of years to **est**imate **prev**ious year's chill days for the first year. `Menzel` requires the number of chill days of previous November and December. With `est_prev = 0` the first year in the time series is used as previous year and dropped from the time series. To keep the first year, chill days from the previous year can be estimated as an average of the first `n` years, when setting argument `est_prev = n`.

## Reference

Menzel, A. (1997) Phänologie von Waldbäumen unter sich ändernden Klimabedingungen - Auswertung der Beobachtungen in den Internationalen Phänologischen Gärten und Möglichkeiten der Modellierung von Phänodaten. *Forstliche Forschungsberichte München*.
