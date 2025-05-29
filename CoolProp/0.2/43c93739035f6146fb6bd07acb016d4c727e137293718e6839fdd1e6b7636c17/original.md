```
set_config(key::AbstractString, val::AbstractString)
```

Set configuration string.

# Arguments

  * `key::AbstractString`: The key to configure, following table shows possible `key` values, its default setting and its usage.
  * `val::AbstractString`: The value to set to the key

| Key                              | Default | Description                                                                                                                                                                                                                |
|:-------------------------------- |:-------:|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| ALTERNATIVE*TABLES*DIRECTORY     |   ""    | If provided, this path will be the root directory for the tabular data.  Otherwise, :({HOME})/.CoolProp/Tables is used                                                                                                     |
| ALTERNATIVE*REFPROP*PATH         |   ""    | An alternative path to be provided to the directory that contains REFPROP's fluids and mixtures directories.  If provided, the SETPATH function will be called with this directory prior to calling any REFPROP functions. |
| ALTERNATIVE*REFPROP*HMX*BNC*PATH |   ""    | An alternative path to the HMX.BNC file.  If provided, it will be passed into REFPROP's SETUP or SETMIX routines                                                                                                           |
| VTPR*UNIFAC*PATH                 |   ""    | The path to the directory containing the UNIFAC JSON files.  Should be slash terminated                                                                                                                                    |
