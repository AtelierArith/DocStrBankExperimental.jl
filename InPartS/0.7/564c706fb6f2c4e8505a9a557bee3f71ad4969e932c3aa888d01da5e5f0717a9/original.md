BackupCallback(backend, filename; [interval = 300.0], [offset = 0.0], [warn = IOWARN[]]) Creates a [`BackupCallback`](@ref) that periodically dumps the entire simulation state to `filename`.

Uses a [`RealTimeCallback`](@ref) with the given `interval` and `offset`.
