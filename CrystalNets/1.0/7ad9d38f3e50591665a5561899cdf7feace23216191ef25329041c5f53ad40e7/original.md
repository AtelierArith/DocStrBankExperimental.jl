```
empty_default_archive!(; refresh=true)
```

Empty the default archive. This will prevent CrystalNets from recognizing any topology before they are explicitly added.

The `refresh` optional parameter controls whether the current archive should also be emptied.

!!! warning
    This empty archive will be kept and used for subsequent runs of CrystalNets.jl, even if you restart your Julia session. If you only want to empty the current archive, do `empty!(CrystalNets.CRYSTALNETS_ARCHIVE)`.

