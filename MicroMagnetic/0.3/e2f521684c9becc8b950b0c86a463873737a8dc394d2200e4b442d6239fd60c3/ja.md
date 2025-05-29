```
save_ovf(sim::AbstractSim, fname::String; type::DataType = Float64)
```

スピンをovf形式で保存し、Muviewで表示できます。

パラメータ:

```
Sim : 保存するスピンを持つSim構造体。

fname : 保存ファイル名。
```

オプション:

```
type : ovf2ファイルのデータ型。Float32、Float64、またはStringから選択できます。
```

例えば:

````
```julia
    save_ovf(sim, "ovf_example")
```
````

または特定のデータ型を指定するには:

````
```julia
    save_ovf(sim, "ovf_example", type = String)
```
````
