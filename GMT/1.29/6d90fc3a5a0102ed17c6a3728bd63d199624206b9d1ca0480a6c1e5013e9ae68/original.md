```
gmtconnect(cmd0::String="", arg1=nothing, kwargs...)
```

Connect individual lines whose end points match within tolerance

## Parameters

  * **C** | **closed** :: [Type => Str | []]        `Arg = [closed]`

    Write all the closed polygons to closed [gmtgmtconnect_closed.txt] and return all other   segments as they are. No gmtconnection takes place.
  * **D** | **dump** :: [Type => Str | []]   `Arg = [template]`

    For multiple segment data, dump each segment to a separate output file
  * **L** | **links** | **linkfile** :: [Type => Str | []]      `Arg = [linkfile]`

    Writes the link information to the specified file [gmtgmtconnect_link.txt].
  * **Q** | **list** | **listfile** :: [Type => Str | []]      `Arg =  [listfile]`

    Used with **D** to write a list file with the names of the individual output files.
  * **T** | **tolerance** :: [Type => Str | List]    `Arg = [cutoff[unit][/nn_dist]]`

    Specifies the separation tolerance in the data coordinate units [0]; append distance unit.   If two lines has end-points that are closer than this cutoff they will be joined.

To see the full documentation type: $@? gmtconnect$
