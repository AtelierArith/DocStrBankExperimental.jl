```
gmtset(; kwargs...)
```

Adjust individual GMT defaults settings in the current directory’s gmt.conf file.

See full GMT (not the `GMT.jl` one) docs at [`gmtset`](http://docs.generic-mapping-tools.org/latest/gmtset.html)

## Parameters

  * **D** | **units** :: [Type => Str | []]

    Modify the GMT defaults based on the system settings. Append u for US defaults or s for SI defaults.
  * **G** | **defaultsfile** :: [Type => Str]

    Name of specific gmt.conf file to read and modify.
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    Select verbosity level, which will send progress reports to stderr.
  * **write** | **|>** :: [Type => Str]     $Arg = fname$

    Save result to ASCII file instead of returning to a Julia variable. Give file name as argument.   Use the bo option to save as a binary file.

### Example:

```
gmtset(FONT_ANNOT_PRIMARY="12p,Helvetica", MAP_GRID_CROSS_SIZE_PRIMARY=0.25)
```
