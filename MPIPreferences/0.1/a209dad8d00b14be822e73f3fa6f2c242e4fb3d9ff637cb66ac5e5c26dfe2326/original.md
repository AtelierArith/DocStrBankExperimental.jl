```
use_jll_binary([binary]; export_prefs=false, force=true)
```

Switches the underlying MPI implementation to one provided by JLL packages. A restart of Julia is required for the changes to take effect.

Available options are:

  * `"MicrosoftMPI_jll"` (Only option and default on Winddows)
  * `"MPICH_jll"` (Default on all other platform)
  * `"OpenMPI_jll"`
  * `"MPItrampoline_jll"`

The `export_prefs` option determines whether the preferences being set should be stored within `LocalPreferences.toml` or `Project.toml`.
