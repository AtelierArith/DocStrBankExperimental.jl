```
FEVector{T}(FES; name = "auto") where T <: Real
```

FESが単一のFESpaceである場合は1つのブロックを持つFEVectorを作成し、FESがFESpaceのベクトルである場合はブロックごとのFEVectorを作成します。オプションで、ベクトルの名前（文字列として）や各ブロックの名前（文字列のベクトルとして）を指定できます。
