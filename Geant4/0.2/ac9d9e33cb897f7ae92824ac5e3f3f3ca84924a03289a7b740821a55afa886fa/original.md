```
initialize(app::G4JLApplication)
```

Initialize the Geant4 application. It initializes the `G4RunManager``, which constructs the detector geometry, and sets  the declared sensitive detectors. In case of multi-threading, the function enters a GC safe state before initializing the application, which will be calling the`build()` functions by the worker threads.

# Arguments

  * `app::G4JLApplication`: Geant4 application
