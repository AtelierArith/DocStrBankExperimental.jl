```julia
add_velocities!(frame::Chemfiles.Frame)

```

この `frame` に速度を追加します。ストレージは、原子の数として `size(frame)` の結果で初期化されます。フレームにすでに速度がある場合、これは何もしません。
