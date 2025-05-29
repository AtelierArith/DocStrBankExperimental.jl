```
integrate_material!(material::AbstractMaterial)
```

Integrate one timestep. The input `material.variables` represents the old problem state.

Abstract method. Must be implemented for each material type. When integration is done, the method **must** write the new state into `material.variables_new`.

**Do not** write into `material.variables`; actually committing the timestep (i.e. accepting that one step of time evolution and applying it permanently) is the job of `update_material!`.
