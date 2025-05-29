```
run_geant4_simulation(app::Geant4.G4JLApplication, number_of_events::Int; energy_threshold::Unitful.Energy)
```

Simulates the given `Geant4.G4JLApplication` until `number_of_events` events with non-zero energy depositions have been generated.

## Arguments

  * `app::Geant4.G4JLApplication`: Contains information about the detector setup and the particle source.
  * `number_of_events::Int`: The amount of events inside of the detector that should be recorded.

## Keywords

  * `energy_threshold::Unitful.Energy`: Defines a lower threshold on the summed energy of an event to be recorded.  Default is `eps(Float64)*u"keV"`, i.e. all events with non-zero deposits are recorded.  If set to `0u"keV"`, all primary events will be recorded.

## Examples

```julia
run_geant4_simulation(app, 1000)
# => returns all events in a `TypedTables.Table` with the fields `evtno`, `detno`, `thit, `edep` and `pos`
```

!!! note
    Since the function is running until enough events have been collected, setups in which the source     does not irradiate the detector will run indefinitely.

