```
Trench structure
```

Structure that defines the geometry of the trench and the slab.

# Parameters

  * `Start`     - Start of the trench (`x`,`y`) coordinates
  * `End`       - End of the trench (`x`,`y`) coordinates
  * `n_seg`     - The number of segment through which the slab is discretize along the dip
  * `Length`    - The length of the slab
  * `Thickness` - The thickness of the slab
  * `Lb`        - Critical distance through which apply the bending angle functions Lb ∈ [0,Length];
  * `θ_max`     - maximum angle of bending ∈ [0°,90°].
  * `direction` - the direction of the dip              The rotation of the coordinate system is done as such that the new X is parallel to the segment. Since the              rotation is anticlockwise the coordinate y has specific values: direction tells if the subduction is directed along              the positive or negative direction of the new y coordinate system. In practice, it apply an additional transformation              to y by multiplying it with -1 or +1;
  * `d_decoupling` - depth at which the slab is fully submerged into the mantle.
  * `type_bending` - is the type of bending angle of the slab [`:Linear`, `:Ribe`].   The angle of slab changes as a function of `l` (∈ [0,Length]). `l` is the actual distance along the slab length from   the trench.   In case:       - `:Linear`           `math θ(l) = ((θ_max - 0.0)/(Lb-0))*l`;       - `:Ribe`           `math θ(l) =  θ_max*l^2*((3*Lb-2*l))/(Lb^3)`;           which is taken from Ribe 2010 [Bending mechanics and mode selection in free subduction: a thin-sheet analysis]

    For l>Lb, θ(l) = θ_max;
  * `WeakzoneThickness` - Thickness of the weakzone [km]
  * `WeakzonePhase` - Phase of the weakzone
