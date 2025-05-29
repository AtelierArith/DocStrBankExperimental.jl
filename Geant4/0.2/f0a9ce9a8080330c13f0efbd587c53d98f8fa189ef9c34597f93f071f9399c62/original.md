```
G4JLApplication(<keyword arguments>)
```

Initialize a G4JLApplication with its associated tyopes and methods.

# Arguments

  * `detector::G4JLDetector`: detector description object
  * `simdata=G4JLNoData()`: simulation data object
  * `generator=G4JLParticleGun()`: primary particle generator
  * `field=nothing`: magnetic field
  * `evtdisplay=nothing`: event display (visualization)
  * `nthreads=0`: number of Geant4 worker threads ( >0 implies MT)
  * `verbose=0` : default verbority level (physics, ...)
  * `runmanager_type=G4RunManager`: run manager type
  * `builder_type=G4JLDetectorConstruction`: detector builder type (the default should be fine most cases)
  * `physics_type=FTFP_BERT`: physics list type
  * `stepaction_type=G4JLSteppingAction`: stepping action type (the default should be fine most cases)
  * `trackaction_type=G4JLTrackingAction`: rtacking action type (the default should be fine most cases)
  * `runaction_type=G4JLRunAction`: run action type (the default should be fine most cases)
  * `eventaction_type=G4JLEventAction`: event action type (the default should be fine most cases)
  * `stepaction_method=nothing`: stepping action method with signature `(::G4Step, ::G4JLApplication)::Nothing`
  * `pretrackaction_method=nothing`: pre-tracking action method with signature `(::G4Track, ::G4JLApplication)::Nothing`
  * `posttrackaction_method=nothing`: post-tracking action method with signature `(::G4Track, ::G4JLApplication)::Nothing`
  * `beginrunaction_method=nothing`: begin run action method with signature `(::G4Run, ::G4JLApplication)::Nothing`
  * `endrunaction_method=nothing`: end run action method with signature `(::G4Run, ::G4JLApplication)::Nothing`
  * `begineventaction_method=nothing`: begin event action method with signature `(::G4Event, ::G4JLApplication)::Nothing`
  * `endeventaction_method=nothing`: end event action method with signature `(::G4Event, ::G4JLApplication)::Nothing`
  * `stackaction_method=nothing`: stacking classification of new track with signature `(::G4Track, ::G4JLApplication)::G4ClassificationOfNewTrack`
  * `statechange_method=nothing`: state change notifycation method with  signature `(from::G4ApplicationState, to::G4ApplicationState, ::G4JLApplication)::Bool`
  * `sdetectors::Vector{}=[]`: vector of pairs `lv::String => sd::G4JLSensitiveDetector` to associate logical volumes to sensitive detector
  * `scorers::Vector{}=[]`: vector of [`G4JLScoringMesh`](@ref)s
