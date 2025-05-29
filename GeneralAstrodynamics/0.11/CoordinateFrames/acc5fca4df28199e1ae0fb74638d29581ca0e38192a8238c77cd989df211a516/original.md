A simple convenience macro for defining new coordinate frames in space. Creates a new `abstract` sub-type of the final argument, `property`.

# Extended Help

**Usage**

`@frame <name>` `@frame <name> is <property>`

Here, `<property>` is previously defined `OrbitalFrame`. which must all be subtypes of `OrbitalFrames.OrbitalFrame`. By using the shortened syntax, `@frame <name>`, your new `abstract`  type `<name>` will only have `OrbitalFrames.OrbitalFrame` as a `supertype`.

**Examples**

```julia
@frame AbstractFrame # second argument defaults to the top-level `OrbitalFrame`
@frame EarthCenteredInertial is BodycentricInertial
@frame SunEarthSynodic is BarycentricInertial
```
