```
psconvert(cmd0::String="", arg1=nothing; kwargs...)
```

Place images or EPS files on maps.

## Parameters

  * **A** | **adjust** | **crop** :: [Type => Str or Number]  

    Adjust the BoundingBox and HiResBoundingBox to the minimum required by the image content.
  * **C** | **gs_option** :: [Type => Str or Array os strings]

    Specify a single, or an araay of, custom option that will be passed on to GhostScript as is.
  * **D** | **out_dir** | **output_dir** :: [Type => Str]

    Sets an alternative output directory (which must exist) [Default is the same directory   as the PS files].
  * **E** | **dpi** :: [Type => Number]

    Set raster resolution in dpi [default = 720 for PDF, 300 for others].
  * **F** | **:out_name** | **output_name** :: [Type => Str]

    Force the output file name.
  * **G** | **ghost_path** :: [Type => Bool]

    Full path to your GhostScript executable.
  * **I** | **resize** :: [Type => Bool]

    Adjust the BoundingBox and HiResBoundingBox by scaling and/or adding margins.
  * **in_memory** :: [Type => Bool]

    Process a in memory PS file. No other input file should be provided.   Currently works on Windows only.
  * **L** | **list_file** :: [Type => Str]

    The listfile is an ASCII file with the names of the PostScript files to be converted.
  * **M** | **embed**

    Sandwich the current psfile between an optional background (-Mb) and optional foreground (-Mf) Postscript plots.
  * **N** | **bgcolor**

    Set optional BoundingBox background fill color, fading, or draw the outline of the BoundingBox.
  * **Q** | **anti_aliasing** :: [Type => Str]

    Set the anti-aliasing options for graphics or text. Append the size of the subsample box   (1, 2, or 4) [4]. This option is set by default.
  * **S** | **gs_command** :: [Type => Bool]

    Print to standard error the GhostScript command after it has been executed.
  * **T** | **format** :: [Type => Str]

    b|e|E|f|F|j|g|G|m|s|t Sets the output format, where b = BMP, e = EPS, E = EPS with PageSize command,   f = PDF, F = multi-page PDF, j = JPEG, g = PNG, G = transparent PNG (untouched regions are   transparent), m = PPM,  and t = TIFF [default is JPEG].   Alternatively, the format may be set with the *fmt* keyword, e.g. *fmt=:png*.
  * **W** | **world_file** :: [Type => Str]

    Write a ESRI type world file suitable to make (e.g) .tif files be recognized as geotiff by   software that know how to do it.
  * **kml** :: [Type => Str | []]

    Create a minimalist KML file that allows loading the image in GoogleEarth.
  * **Z** | **del*input*ps** :: [Type => Bool]

    Remove the input PostScript file(s) after the conversion.
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    Select verbosity level, which will send progress reports to stderr.

To see the full documentation type: $@? psconvert$
