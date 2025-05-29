```
pvd = movie_paraview(; name="Movie", pvd=pvd, Finalize::Bool=false, Initialize::Bool=true)
```

データセットのムービーを作成したい場合は、このルーチンを使用してムービーファイルを初期化および最終化できます。これにより、Paraviewで開くことができる`*.pvd`ファイルが作成されます。

個々のタイムステップは、`pvd`とタイムステップの時間を`write_paraview`ルーチンに渡すことでムービーに追加されます。

# 例

通常、これは`*.jl`スクリプト内で使用されます。以下は擬似例です：

```julia
movie = movie_paraview(name="Movie", Initialize=true)
for itime=1:10
    name = "test"*string(itime)
    movie = write_paraview(Data, name, pvd=movie, time=itime)
end
movie_paraview(pvd=movie, Finalize=true)
```
