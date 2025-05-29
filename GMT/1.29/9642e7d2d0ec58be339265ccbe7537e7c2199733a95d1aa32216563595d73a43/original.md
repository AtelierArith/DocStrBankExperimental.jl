```
gmtwhich(cmd0::String; kwargs...)
```

Find full path to specified files

See full GMT (not the `GMT.jl` one) docs at [`gmtwhich`](http://docs.generic-mapping-tools.org/latest/gmtwhich.html)

## Parameters

  * **A** | **readable** :: [Type => Bool]

```
Only consider files that the user has permission to read [Default consider all files found].
```

  * **C** | **confirm** :: [Type => Bool]

```
Instead of reporting the paths, print the confirmation Y if the file is found and N if it is not.
```

  * **D** | **report_dir** :: [Type => Bool]

```
Instead of reporting the paths, print the directories that contains the files.
```

  * **G** | **download** :: [Type => Str | []]      $Arg = [c|l|u]$

```
If a file argument is a downloadable file (either a full URL, a @file for downloading from
the GMT Site Cache, or @earth_relief_*.grd) we will try to download the file if it is not
found in your local data or cache dirs.
```

  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    Select verbosity level, which will send progress reports to stderr.
