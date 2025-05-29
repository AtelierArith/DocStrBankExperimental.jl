```
set_config(key::AbstractString, val::Bool)
```

Set configuration value as a boolean.

# Arguments

  * `key::AbstractString`: The key to configure, following table shows possible `key` values, its default setting and its usage.
  * `val::Bool`: The value to set to the key

| Key                                                   | Default | Description                                                                                                                                                                         |
|:----------------------------------------------------- |:-------:|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| NORMALIZE*GAS*CONSTANTS                               |  true   | If true, for mixtures, the molar gas constant (R) will be set to the CODATA value                                                                                                   |
| CRITICAL*WITHIN*1UK                                   |  true   | If true, any temperature within 1 uK of the critical temperature will be considered to be AT the critical point                                                                     |
| CRITICAL*SPLINES*ENABLED                              |  true   | If true, the critical splines will be used in the near-vicinity of the critical point                                                                                               |
| SAVE*RAW*TABLES                                       |  false  | If true, the raw, uncompressed tables will also be written to file                                                                                                                  |
| REFPROP*DONT*ESTIMATE*INTERACTION*PARAMETERS          |  false  | If true, if the binary interaction parameters in REFPROP are estimated, throw an error rather than silently continuing                                                              |
| REFPROP*IGNORE*ERROR*ESTIMATED*INTERACTION_PARAMETERS |  false  | If true, if the binary interaction parameters in REFPROP are unable to be estimated, silently continue rather than failing                                                          |
| REFPROP*USE*GERG                                      |  false  | If true, rather than using the highly-accurate pure fluid equations of state, use the pure-fluid EOS from GERG-2008                                                                 |
| REFPROP*USE*PENGROBINSON                              |  false  | If true, rather than using the highly-accurate pure fluid equations of state, use the Peng-Robinson EOS                                                                             |
| DONT*CHECK*PROPERTY_LIMITS                            |  false  | If true, when possible, CoolProp will skip checking whether values are inside the property limits                                                                                   |
| HENRYS*LAW*TO*GENERATE*VLE_GUESSES                    |  false  | If true, when doing water-based mixture dewpoint calculations, use Henry's Law to generate guesses for liquid-phase composition                                                     |
| OVERWRITE_FLUIDS                                      |  false  | If true, and a fluid is added to the fluids library that is already there, rather than not adding the fluid (and probably throwing an exception), overwrite it                      |
| OVERWRITE*DEPARTURE*FUNCTION                          |  false  | If true, and a departure function to be added is already there, rather than not adding the departure function (and probably throwing an exception), overwrite it                    |
| OVERWRITE*BINARY*INTERACTION                          |  false  | If true, and a pair of binary interaction pairs to be added is already there, rather than not adding the binary interaction pair (and probably throwing an exception), overwrite it |
