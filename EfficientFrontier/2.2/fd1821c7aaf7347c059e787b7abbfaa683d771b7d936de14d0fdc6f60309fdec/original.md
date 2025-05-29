```
   ECL!(aCL::Vector{sCL{T}}, PS::Problem{T}; numSettings = Settings(PS), incL=false, settings=SettingsQP(PS), settingsLP=SettingsLP(PS))  where T
```

compute all the Critical Line Segments as L decreasing to 0 (increasing to +Inf if incL=true), given the first one in aCL[end].  The `settings` is the `LightenQP.Settings` setting from LightenQP Return value: true if done
