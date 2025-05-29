```
label(obj) -> Vector
```

与えられたオブジェクト `obj` に表されるラベルを返します。ラベルの順序が重要であることに注意してください。2つのラベルの場合、最初の要素は正のラベルを表し、2番目の要素は負のラベルを表します。

```
julia> label([:yes,:no,:yes,:yes])
2-element Array{Symbol,1}:
 :yes
 :no

julia> label(LabelEnc.ZeroOne())
2-element Array{Float64,1}:
 1.0
 0.0
```
