```
close_h5file!(sim::Simulation)
```

シミュレーション `sim` に添付された HDF5 ファイルを閉じます。

次に [`write_`](@ref) 関数のいずれか（例えば [`write_snapshot`](@ref））を呼び出すと、自動的に新しいファイルが作成され、[`create_simulation`](@ref) の `overwrite_file` 引数に応じて、閉じたファイルが上書きされることに注意してください。
