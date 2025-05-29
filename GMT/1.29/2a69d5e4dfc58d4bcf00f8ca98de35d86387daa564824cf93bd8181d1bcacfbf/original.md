```
grd2cpt(cmd0::String="", arg1=nothing, kwargs...)
```

Make linear or histogram-equalized color palette table from grid

## Parameters

  * **A** | **alpha** | **transparency** :: [Type => Str]

    Sets a constant level of transparency (0-100) for all color slices.
  * **C** | **color** | **colormap** | **cmap** | **colorscale** :: [Type => Str]	$Arg = [cpt |master[+izinc] |color1,color2[,*color3*,…]]$

    Give a CPT name or specify -Ccolor1,color2[,color3,...] to build a linear continuous CPT from those   colors automatically.
  * **D** | **bg** | **background** :: [Type => Str | []]			`Arg = [i|o]`

    Select the back- and foreground colors to match the colors for lowest and highest   z-values in the output CPT.
  * **E** | **nlevels** :: [Type => Int | []]		`Arg = [nlevels]`

    Create a linear color table by using the grid z-range as the new limits in the CPT.   Alternatively, append nlevels and we will resample the color table into nlevels equidistant slices.
  * **F** | **color_model** :: [Type => Str | []]		`Arg = [R|r|h|c][+c]]`

    Force output CPT to written with r/g/b codes, gray-scale values or color name.
  * **G** | **truncate** :: [Type => Str]             `Arg = zlo/zhi`

    Truncate the incoming CPT so that the lowest and highest z-levels are to zlo and zhi.
  * **I** | **inverse** | **reverse** :: [Type => Str]	    `Arg = [c][z]`

    Reverse the sense of color progression in the master CPT.
  * **L** | **datarange** | **clim** :: [Type => Str]			`Arg = minlimit/maxlimit`

    Limit range of CPT to minlimit/maxlimit, and don’t count data outside this range when estimating CDF(Z).   [Default uses min and max of data.]
  * **M** | **overrule_bg** :: [Type => Bool]

    Overrule background, foreground, and NaN colors specified in the master CPT with the values of   the parameters COLOR*BACKGROUND, COLOR*FOREGROUND, and COLOR_NAN.
  * **N** | **no_bg** | **nobg** :: [Type => Bool]

    Do not write out the background, foreground, and NaN-color fields.
  * **Q** | **log** :: [Type => Bool]

    Selects a logarithmic interpolation scheme [Default is linear].
  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    Specify the region of interest. Set to data minimum BoundinBox if not provided.
  * **S** | **symmetric** :: [Type => Str]			`Arg = h|l|m|u`

    Force the color table to be symmetric about zero (from -R to +R).
  * **T** | **range** :: [Type => Str]			`Arg = (min,max,inc) or = "n"`

    Set steps in CPT. Calculate entries in CPT from zstart to zstop in steps of (zinc). Default   chooses arbitrary values by a crazy scheme based on equidistant values for a Gaussian CDF.
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    Select verbosity level, which will send progress reports to stderr.
  * **W** | **categorical** :: [Type => Bool | Str | []]      `Arg = [w]`

    Do not interpolate the input color table but pick the output colors starting at the   beginning of the color table, until colors for all intervals are assigned.
  * **Z** | **continuous** :: [Type => Bool]

    Creates a continuous CPT [Default is discontinuous, i.e., constant colors for each interval].
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    Select verbosity level, which will send progress reports to stderr.
  * **write** | **|>** :: [Type => Str]     $Arg = fname$

    Save result to ASCII file instead of returning to a Julia variable. Give file name as argument.   Use the bo option to save as a binary file.

To see the full documentation type: $@? grd2cpt$
