```
convertlabel(new_encoding, x, [old_encoding])
```

指定された値/配列 `x` を `old_encoding` から `new_encoding` に変換します。`old_encoding` が指定されていない場合は、`labelenc` を使用して自動的に導出されます。

```
julia> convertlabel(LabelEnc.MarginBased, [0, 1, 1, 0, 0])
5-element Array{Int64,1}:
 -1
  1
  1
 -1
 -1

julia> convertlabel([:yes,:no], [0, 1, 1, 0, 0])
5-element Array{Symbol,1}:
 :no
 :yes
 :yes
 :no
 :no
```

利用可能なエンコーディングの詳細については、`?LabelEnc` を参照してください。

```
convertlabel(new_encoding, x, [old_encoding], [obsdim])
```

`OneOfK` を使用する場合、`obsdim` を使用して配列のどの次元が観測を示すかを追加で指定できます。

```
julia> convertlabel(LabelEnc.OneOfK, [0, 1, 1, 0, 0], obsdim = 2)
2×5 Array{Int64,2}:
 0  1  1  0  0
 1  0  0  1  1
```
