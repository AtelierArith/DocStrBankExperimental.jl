```julia
Trajectory(f::Function, args...) -> Any

```

`f`を`Trajectory(args...)`の結果に適用し、完了時に結果の軌道を閉じます。これは`open(f, args...)`に似ています。
