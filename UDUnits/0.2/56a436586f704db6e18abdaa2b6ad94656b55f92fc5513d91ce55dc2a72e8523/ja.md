```
system = System()
```

デフォルトのSI単位系をロードします。`system`は辞書に似た動作をし、インデックス付けと関数`haskey`（単位が有効かどうかを判断するため）をサポートします：

```julia
using UDUnits
sys = System()
m = sys["meter"]
haskey(sys,"μm") # returns true
```
