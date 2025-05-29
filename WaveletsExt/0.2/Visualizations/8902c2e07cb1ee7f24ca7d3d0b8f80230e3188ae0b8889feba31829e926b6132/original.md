```
wiggle!(wav[; taxis, zaxis, sc, EdgeColor, FaceColor, Orient, Overlap, ZDir])
wiggle!(plt, wav[; taxis, zaxis, sc, EdgeColor, FaceColor, Orient, Overlap, ZDir])
```

Plot a set of shaded wiggles on the current displayed graphics or on top of `plt`. If there are no displayed graphics currently available, a new `Plots.Plot` object is generated to plot the shaded wiggles.

# Arguments

  * `plt::Plots.Plot`: Input plot to plot shaded wiggles.
  * `wav::AbstractArray{<:Number,2}`: Matrix of waveform columns.

# Keyword Arguments

  * `taxis::AbstractVector`: (Default: `1:size(wav,1)`) Time axis vector
  * `zaxis::AbstractVector`: (Default: `1:size(wav,2)`) Space axis vector
  * `sc::Real`: (Default: `1`) Scale factor/magnification.
  * `EdgeColor::Symbol`: (Default: `:black`) Sets edge of wiggles color.
  * `FaceColor::Symbol`: (Default: `:black`) Sets shading color of wiggles.
  * `Overlap::Bool`: (Default: `true`) How signals are scaled.

      * `true`  - Signals overlap (default);
      * `false` - Signals are scaled so they do not overlap.
  * `Orient::Symbol`: (Default: `:across`) Controls orientation of wiggles.

      * `:across` - from left to right
      * `:down`   - from top to down
  * `ZDir::Symbol`: (Default: `:normal`) Direction of space axis.

      * `:normal`  - First signal at bottom (default)
      * `:reverse` - First signal at top.

# Returns

`::Plots.Plot`: Shaded wiggles on top of current plot object.

# Examples

```julia
using Plots, WaveletsExt

# Generate random signals
x = randn(16, 5)

# ----- Build wiggles -----
# Build onto existing plot
plt = plot()
wiggle!(x)

# Build onto a specified plot
wiggle!(plt, x)
```

Translated by Nicholas Hausch – MATLAB file provided by Naoki Saito. The previous MATLAB version contributors are Anthony K. Booer (SLB) and Bradley Marchand (NSWC-PC).  

Revised by Naoki Saito, Feb. 05, 2018. Maintained by Zeng Fung Liew for newest Julia version compatibility. 

**See also:** [`wiggle`](@ref)
