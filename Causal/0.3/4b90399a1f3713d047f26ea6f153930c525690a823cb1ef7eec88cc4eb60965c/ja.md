```julia
addnode!(model, component; label)

```

`model`にノードを追加します。コンポーネントは`component`で、`label`はノードのラベルである`label`です。追加されたノードを返します。

# 例

```jldoctest
julia> model = Model()
Model(numnodes:0, numedges:0, timesettings=(0.0, 0.01, 1.0))

julia> addnode!(model, SinewaveGenerator(), label=:gen)
Node(component:SinewaveGenerator(amp:1.0, freq:1.0, phase:0.0, offset:0.0, delay:0.0), idx:1, label:gen)
```
