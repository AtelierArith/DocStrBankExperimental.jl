```
writeframe(io, trcs, idx...)
```

`io::JSeis`に対応するJavaSeisデータセットにデータのフレームを書き込みます。`trcs`は2次元配列です。書き込まれるデータセットの位置は`idx...`によって決まります。例えば：

# 3D:

```julia
writeframe(jsopen("data_3D.js"), trcs, 1) # フレーム1に書き込む
```

# 4D:

```julia
writeframe(jsopen("data_4D.js"), trcs, 1, 2) # フレーム1、ボリューム2に書き込む
```

# 5D:

```julia
writeframe(jsopen("data_5D.js"), trcs, 1, 2, 3) # フレーム1、ボリューム2、ハイパーキューブ3に書き込む
```
