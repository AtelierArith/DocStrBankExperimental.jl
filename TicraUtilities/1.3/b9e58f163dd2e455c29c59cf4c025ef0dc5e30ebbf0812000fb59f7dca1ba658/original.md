```
eh2bor1cut(theta, fe, fh; kwargs...) -> cut::Cut
```

Create a [`Cut`](@ref) object for a "BOR1" horn from its E-plane and H-plane patterns.

A "BOR₁" horn is circularly symmetric and contains only TE₁ₙ and TM₁ₙ waveguide modes in its  radiating aperture.  It's radiated far field can therefore be expressed in terms of the E-plane and H-plane patterns it radiates when excited for linear polarization.

## Positional Input Arguments

  * `theta`: A vector or range (an `AbstractVector`) of θ values (in degrees) at which the cut  pattern should be evaluated. The first element of `theta` must be 0, and the entries must  be equally spaced, as in a `range` object.
  * `fe`, `fh`: The E-plane and H-plane patterns, resp.  These are either both `AbstractVector`s of the  same length as `theta`, or both functions which take a single input θ (in degrees) and return the  respective patterns evaluated at that angle.

## Keyword Arguments

  * `pol`: Defines the manner in which the horn is assumed to be excited, and the polarization basis  selected for use in the output `Cut`.  `pol` is a `String` or `Symbol` taking one of the values (capitalization is not significant):

      * "l3v" or `:l3v`: (the default value) The horn is excited for "vertical" (y-directed) linear polarization  and the far field is expressed as Ludwig-3 components.
      * "l3h" or `:l3h`: The horn is excited for "horizontal" (x-directed) linear polarization and the far field is expressed as Ludwig-3 components.
      * "rhcp" or `:rhcp`: The horn is excited for RHCP (right-hand circular polarization) and the far field is expressed as RHCP and LHCP components.
      * "lhcp" or `:lhcp`: The horn is excited for LHCP (left-hand circular polarization) and the far field is expressed as RHCP and LHCP components.

    If linear (circular) polarization is requested, then the output `Cut` object will contain eight (four) cuts, spaced every 45° (90°).
  * `xpd`: The crosspol level in dB < 0. Defaults to `-Inf` (negative infinity).  If finite, then in addition to the specified polarization, a crosspolarized contribution will be added to the cut, as if the horn is fed by an imperfect feed network with the specified crosspol level.
  * `xpphase`: The phase (in degrees) of the crosspol contribution whose amplitude is specified by `xpd`.
