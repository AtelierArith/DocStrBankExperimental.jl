```
set_config(key::AbstractString, val::Real)
```

Set configuration numerical value as double.

# Arguments

  * `key::AbstractString`: The key to configure, following table shows possible `key` values, its default setting and its usage.
  * `val::Real`: The value to set to the key

| Key                                 |  Default  | Description                                                                                                                                                                                  |
|:----------------------------------- |:---------:|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| MAXIMUM*TABLE*DIRECTORY*SIZE*IN_GB  |    1.0    | The maximum allowed size of the directory that is used to store tabular data                                                                                                                 |
| PHASE*ENVELOPE*STARTING*PRESSURE*PA |   100.0   | Starting pressure [Pa] for phase envelope construction                                                                                                                                       |
| R*U*CODATA                          | 8.3144598 | The value for the ideal gas constant in J/mol/K according to CODATA 2014.  This value is used to harmonize all the ideal gas constants. This is especially important in the critical region. |
| SPINODAL*MINIMUM*DELTA              |    0.5    | The minimal delta to be used in tracing out the spinodal; make sure that the EOS has a spinodal at this value of delta=rho/rho_r                                                             |
