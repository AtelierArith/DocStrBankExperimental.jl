```
parse_settings!(settings_cfgs::Vector{ArgParseSettings}=mhlib_settings_cfgs; args=ARGS)
```

Parses the arguments and initializesn the global `settings` correspondingly,

Also initializes the random number generator, if `settings[:seed] != 0` randomly. In `settings_cfgs` a list of the ArgParseSettings of individual modules to be used in addition to the basic `settings_cfg` of this module has to be provided. `MHLib.mhlib_settings_cfgs` can be used to include all settings of all modules.
