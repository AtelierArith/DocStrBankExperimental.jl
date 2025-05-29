```
EventParameters(; comment, event, description, creation_info, public_id)
```

Root type of QuakeML.  `EventParameters` objects contain a set of events and a QuakeML XML file can contain only one `EventParameters` object.

In the bulletin-type (non real-time) model, this type serves as a container for `Event` objects. In the real-time version, it can hold objects of type `Event`, `Origin`, `Magnitude`, `StationMagnitude`, `FocalMechanism`, `Reading`, `Amplitude`, and `Pick`.

# List of fields

  * `event :: Vector{Event}`: Set of [`Event`](@ref QuakeML.Event)s making up a catalog or collection of events.
  * `description :: String`: Description string that can be assigned to the earthquake catalog, or collection of events.
  * `comment :: Vector{Comment}`: Additional comments.
  * `creation_info :: CreationInfo`: [`CreationInfo`](@ref QuakeML.CreationInfo) for the earthquake catalog.
  * `public_id :: ResourceReference`: Resource identifier of `EventParameters`. (**Required field.**)

!!! note
    At present, QuakeML.jl only supports the non-real-time version of QuakeML.

