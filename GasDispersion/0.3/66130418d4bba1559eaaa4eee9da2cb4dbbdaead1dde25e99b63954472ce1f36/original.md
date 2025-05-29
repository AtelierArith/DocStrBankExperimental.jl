```
HorizontalJet{<:Number}(;kwargs...)<:Release
```

A simple container for parameters of a horizontal jet release.

# Arguments

  * `mass_rate::Number`: the mass emission rate of the substance, kg/s.
  * `duration::Number`: the duration of the release, s.
  * `diameter::Number`: the diameter of the jet, m.
  * `velocity::Number`: the average velocity of the jet, m/s.
  * `height::Number`: the height of the jet center, m.
  * `pressure::Number`: the pressure at the jet exit, Pa.
  * `temperature::Number`: the temperature at the jet exit, K.
  * `fraction_liquid::Number`: the fraction of the release that is liquid (for gas liquid mixtures), vol fraction.
