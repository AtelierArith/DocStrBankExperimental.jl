```
beamOn(app::G4JLApplication, nevents::Int)
```

Start a new run with `nevents` events. In case of multi-threading, the function enters a GC safe state before starting the run.

# Arguments

  * `app::G4JLApplication`: Geant4 application
  * `nevents::Int`: number of events
