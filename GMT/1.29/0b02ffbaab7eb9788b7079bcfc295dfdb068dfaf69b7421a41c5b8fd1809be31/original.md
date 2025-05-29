```
makecpt(cmd0::String="", arg1=nothing; kwargs...)
```

or

```
makecpt(name::Symbol; kwargs...)
```

Make static color palette tables (CPTs). The second form accepts a name of one of the GMT CPT defaults.

  * **A** | **alpha** | **transparency** :: [Type => Str]

    Sets a constant level of transparency (0-100) for all color slices.
  * **C** | **color** | **colormap** | **cmap** | **colorscale** :: [Type => Str]	$Arg = [cpt |master[+izinc] |color1,color2[,*color3*,…]]$

    Give a CPT name or specify -Ccolor1,color2[,color3,...] to build a linear continuous CPT from those   colors automatically.
  * **D** | **bg** | **background** :: [Type => Str | []]			`Arg = [i|o]`

    Select the back- and foreground colors to match the colors for lowest and highest   z-values in the output CPT.
  * **E** | **nlevels** :: [Type => Int | []]		`Arg = [nlevels]`

    Implies reading data table(s) from file or arrays. We use the last data column to   determine the data range
  * **F** | **color_model** :: [Type => Str | []]		`Arg = [R|r|h|c][+c]]`

    Force output CPT to written with r/g/b codes, gray-scale values or color name.
  * **G** | **truncate** :: [Type => Str]              `Arg = zlo/zhi`

    Truncate the incoming CPT so that the lowest and highest z-levels are to zlo and zhi.
  * **I** | **inverse** | **reverse** :: [Type => Str]	`Arg = [c][z]`

    Reverse the sense of color progression in the master CPT.
  * **M** | **overrule_bg** :: [Type => Bool]

    Overrule background, foreground, and NaN colors specified in the master CPT with the values of   the parameters COLOR*BACKGROUND, COLOR*FOREGROUND, and COLOR_NAN.
  * **N** | **no_bg** | **nobg** :: [Type => Bool]

    Do not write out the background, foreground, and NaN-color fields.
  * **Q** | **log** :: [Type => Bool | Str]			`Arg = [i|o]`

    Selects a logarithmic interpolation scheme [Default is linear].
  * **S** | **auto** :: [Type => Bool | Str]			`Arg = [mode]`

    Determine a suitable range for the -T option from the input table(s) (or stdin).
  * **T** | **range** :: [Type => Str]			`Arg = [min/max/inc[+b|l|n]|file|list]`

    Defines the range of the new CPT by giving the lowest and highest z-value and interval.
  * **W** | **wrap** | **categorical** :: [Type => Bool | Str | []]      `Arg = [w]`

    Do not interpolate the input color table but pick the output colors starting at the   beginning of the color table, until colors for all intervals are assigned.
  * **Z** | **continuous** :: [Type => Bool]

    Creates a continuous CPT [Default is discontinuous, i.e., constant colors for each interval].

To see the full documentation type: $@? makecpt$
