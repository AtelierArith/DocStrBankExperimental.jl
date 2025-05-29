```
setSrcToPoint(yes::Bool)::Bool
```

return whether the source type is a point or not after setting `srcType` to `srcPoint` if  `yes` = `true` else if `yes` = `false` setting it to `srcNotPoint` if it was not already  set to other non-point type (`srcDisk`, `srcLine`, `srcVolume`).

!!! note
      * The user can use this function to change the source type any time.
      * The source type is set the fist time asked for source.


**see also:** [`typeofSrc(::Int)`](@ref).
