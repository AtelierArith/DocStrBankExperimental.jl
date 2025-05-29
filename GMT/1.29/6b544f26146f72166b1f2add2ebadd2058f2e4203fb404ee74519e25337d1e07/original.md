```
gmt2kml(cmd0::String="", arg1=nothing, kwargs...)
```

Convert GMT data tables to KML files for Google Earth

## Parameters

  * **A** | **altitude_mode** :: [Type => Str]       $Arg = a|g|s[alt|xscale]$

    Select one of three altitude modes recognized by Google Earth that determines the altitude (in m)   of the feature: $a$ absolute altitude, $g$ altitude relative to sea surface or ground,   $s$ altitude relative to seafloor or ground.
  * **C** | **color** | **colormap** | **cmap** | **colorscale** :: [Type => Str]	$Arg = [cpt |master[+izinc] |color1,color2[,*color3*,…]]$

    Give a CPT name or specify -Ccolor1,color2[,color3,...] to build a linear continuous CPT from those   colors automatically.
  * **D** | **descript** :: [Type => Str]   $Arg = descriptfile$

    File with HTML snippets that will be included as part of the main description content for the KML file.
  * **E** | **extrude** :: [Type => Str | []]  $Arg = [altitude]$

    Extrude feature down to ground level.
  * **F** | **feature_type** :: [Type => Str]  $Arg = e|s|t|l|p|w$

    Sets the feature type. Choose from points (event, symbol, or timespan), line, polygon, or wiggle.
  * **G** | **fill** :: [Type => Str]  $Arg = f|nfill$

    Sets color fill (G=:f) or label font color (G=:n).
  * **I** | **icon** :: [Type => Str]      $Arg = icon$

    Specify the URL to an alternative icon that should be used for the symbol   [Default is a Google Earth circle].
  * **K** | **not_over** :: [Type => Bool]

    Allow more KML code to be appended to the output later [finalize the KML file].
  * **L** | **extra_data** :: [Type => Str]      $Arg = name1,name2,…$

    Extended data given. Append one or more column names separated by commas.
  * **N** | **feature_name** :: [Type => Str | Number]      $Arg = [t|col |name_template|name]$

    By default, if segment headers contain a -L”label string” then we use that for the name of the KML feature.
  * **O** | **overlay** :: [Type => Bool]

    Append KML code to an existing KML file [initialize a new KML file].
  * **Qa** | **wiggles** :: [Type => Str]      $Arg =  azimuth$

    Option in support of wiggle plots (requires F=:w).
  * **Qs** | **wiggle_scale** :: [Type => Str | Number]      $Arg =  scale[unit]$

    Required setting for wiggle plots (i.e., it requires F=:w). Sets a wiggle scale   in z-data units per the user’s units
  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    Specify the region of interest. Set to data minimum BoundinBox if not provided.
  * **S** | **ilscale** :: [Type => Str]      $Arg =  c|nscale$

    Scale icons or labels. Here, S=:c sets a scale for the symbol icon, whereas S=:n sets   a scale for the name labels
  * **T** | **title** :: [Type => Str]    $Arg = title[/foldername]$

    Sets the document title [default is unset]. Optionally, append /FolderName;
  * **W** | **pen** :: [Type => Str | []]      $Arg =  [pen][attr]$

    Set pen attributes for lines, wiggles or polygon outlines.
  * **Z** | **attrib** :: [Type => Str]      $Arg =  args$

    Set one or more attributes of the Document and Region tags.
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    Select verbosity level, which will send progress reports to stderr.
  * **write** | **|>** :: [Type => Str]     $Arg = fname$

    Save result to ASCII file instead of returning to a Julia variable. Give file name as argument.   Use the bo option to save as a binary file.
  * **append** :: [Type => Str]     $Arg = fname$

    Append result to an existing file named $fname$ instead of returning to a Julia variable.   Use the bo option to save as a binary file.

To see the full documentation type: $@? gmt2kml$
