```julia
write_urdf(io, mechanism; robot_name, include_root)

```

`mechanism`のURDF表現をストリーム`io`（`Base.IO`）に書き込みます。

オプションで、`robot_name`キーワード引数を使用してロボットの名前を指定できます。
