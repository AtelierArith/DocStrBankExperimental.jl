```
clean_default_archive!(custom_arc; validate=true, refresh=true)
```

Erase the default archive used by CrystalNets.jl to recognize known topologies and replace it with a new one from the file located at `custom_arc`.

The `validate` parameter controls whether the new file is checked and converted to a format usable by CrystalNets.jl. If unsure, leave it set.

The `refresh` optional parameter controls whether the current archive should be replaced by the new default one.

!!! warning
    This archive will be kept and used for subsequent runs of CrystalNets.jl, even if you restart your Julia session.

    To only change the archive for the current session, use [`change_current_archive!(custom_arc)`](@ref change_current_archive!).

    See also [`refresh_current_archive!`](@ref) for similar uses.


!!! warning
    The previous default archive cannot be recovered afterwards, so make sure to keep a copy if necessary. The default archive is the set of ".arc" files located at `joinpath(dirname(dirname(pathof(CrystalNets))), "archives")`.

