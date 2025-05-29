```
G4JLScoringMesh(name, mesh; <keyword arguments>)
```

Create a scoring mesh to be added to the Geant4 application.

# Arguments

  * `name::String`: scoring mech name
  * `mesh::AbstractMesh`: mesh instance. Either a `BoxMesh` or `CylinderMesh`
  * `bins::Tuple`: tuple with number on bins in x, y, z (default 30, 30, 30)
  * `translation::Tuple`: position (x,y,z) with respect the mesh respect to the world volume. Default is  (0,0,0).
  * `rotation::Tuple`: rotation of the mesh with respect the world volume. Default (0,0,0)
  * `quantities::Vector`: vector of quanties to be scored (e.g. `energyDeposit`, `doseDeposit`, `nOfStep`)
