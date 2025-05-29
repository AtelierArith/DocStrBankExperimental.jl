```
getnode(model, idx::Int)
```

`idx`のインデックスを持つ`model`のノードを返します。

```
getnode(model, label)
```

`label`のラベルを持つ`model`のノードを返します。

# 例

```jldoctest
julia> model = Model()
Model(numnodes:0, numedges:0, timesettings=(0.0, 0.01, 1.0))

julia> addnode!(model, SinewaveGenerator(), label=:gen)
Node(component:SinewaveGenerator(amp:1.0, freq:1.0, phase:0.0, offset:0.0, delay:0.0), idx:1, label:gen)

julia> addnode!(model, Gain(), label=:gain)
Node(component:Gain(gain:1.0, input:Inport(numpins:1, eltype:Inpin{Float64}), output:Outport(numpins:1, eltype:Outpin{Float64})), idx:2, label:gain)

julia> getnode(model, :gen)
Node(component:SinewaveGenerator(amp:1.0, freq:1.0, phase:0.0, offset:0.0, delay:0.0), idx:1, label:gen)

julia> getnode(model, 2)
Node(component:Gain(gain:1.0, input:Inport(numpins:1, eltype:Inpin{Float64}), output:Outport(numpins:1, eltype:Outpin{Float64})), idx:2, label:gain)
```
