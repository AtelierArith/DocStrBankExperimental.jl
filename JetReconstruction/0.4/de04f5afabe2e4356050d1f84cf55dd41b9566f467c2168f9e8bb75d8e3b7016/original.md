```
savejets(filename, jets; format="px py pz E")
```

Save jet data to a file.

# Arguments

  * `filename`: The name of the file to save the jet data to.
  * `jets`: An array of jet objects to save.
  * `format="px py pz E"`: (optional) A string specifying the format of the jet data to save. The default format is "px py pz E".

# Details

This function saves jet data to a file in a specific format. Each line in the file represents a jet and contains the information about the jet in the specified format. The format string can include the following placeholders:

  * "E" or "energy": Jet energy
  * "px": Momentum along the x-axis
  * "py": Momentum along the y-axis
  * "pz": Momentum along the z-axis
  * "pt2": Square of the transverse momentum
  * "phi": Azimuth angle
  * "rapidity": Rapidity

Lines starting with '#' are treated as comments and are ignored.

It is strongly NOT recommended to put something other than values and (possibly custom) separators in the `format` string.
