MCFlashJL(;     method = MultiComponentFlash.SSIFlash(),     storage = nothing,     V = NaN,     K = nothing,     kwargs.... )

Uses `MultiComponentFlash.jl` two-phase flash solver. allows passing storage to minimize allocations. That storage can be created by calling `MultiComponentFlash.flash_storage(model,p,T,z,method::MCFlashJL)`

!!! note
    This method requires `MultiComponentFlash` to be loaded in the current session (`using MultiComponentFlash`) and julia >= v1.9

