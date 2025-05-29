readsim(f; snap = InPartS.lastfullsnap(f), [warn = IOWARN[]], [kwargs...]) readsim(filename; snap, [warn = IOWARN[]], [kwargs...]) Read a simulation from file and load the specified snapshot. Defaults to the last full snapshot (see [`lastfullsnap`](@ref)).

Additional keyword arguments are passed through to [`readstatic`](@ref) and [`readsnap`](@ref).
