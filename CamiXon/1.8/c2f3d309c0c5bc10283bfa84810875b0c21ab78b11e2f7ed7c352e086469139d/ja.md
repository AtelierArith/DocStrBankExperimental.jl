```
dictConfiguration
```

与えられた (Z, Q) の原子の電子基底状態構成。

```
julia> dictConfiguration
Dict{Int64, String} with 102 entries:
  (5, 0)  => "[Be]2p¹"
  (56, 0) => "[Ba]"
  (35, 0) => "[Zn]4p⁵"
  (55, 0) => "[Na]6s¹"
  (60, 0) => "[Ba]4f⁴"
  (30, 0) => "[Zn]"
  (32, 0) => "[Zn]4p²"
  ⋮  => ⋮
```

#### 例:

```
julia> Z, Q = (get(dictAtomicNumber, "Ta", nothing), 0)
(73, 0)

julia> dict = dictConfiguration;

julia> get(dict, (Z, Q), nothing)
"[Yb]5d³"
```
