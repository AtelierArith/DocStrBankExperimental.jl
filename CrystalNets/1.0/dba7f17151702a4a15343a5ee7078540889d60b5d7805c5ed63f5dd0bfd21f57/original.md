```
change_current_archive!(custom_arc; validate=true)
```

Erase the current archive used by CrystalNets.jl to recognize known topologies and replace it with the archive stored in the file located at `custom_arc`.

The `validate` optional parameter controls whether the new file is checked and converted to a format usable by CrystalNets.jl. If unsure, leave it set.

!!! note
    This modification will only last for the duration of this Julia session.

    If you wish to change the default archive and use it for subsequent runs, use [`clean_default_archive!`](@ref).


!!! warning
    Using an invalid archive will make CrystalNets.jl unusable. If this happens, simply run [`refresh_current_archive!()`](@ref) to revert to the default archive.

