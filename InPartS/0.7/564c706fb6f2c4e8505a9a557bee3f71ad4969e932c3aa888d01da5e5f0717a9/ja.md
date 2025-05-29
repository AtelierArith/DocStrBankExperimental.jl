`BackupCallback(backend, filename; [interval = 300.0], [offset = 0.0], [warn = IOWARN[]])` は、定期的にシミュレーションの全状態を `filename` にダンプする [`BackupCallback`](@ref) を作成します。

指定された `interval` と `offset` を使用して [`RealTimeCallback`](@ref) を使用します。
