```
filter_map(filter_fnc::Function, map_fnc::Function, tree::AbstractNode, result_type::Type, break_sharing::Val=Val(false))
```

中間の割り当てを避ける、`map(map_fnc, filter(filter_fnc, tree))`のより高速な同等物です。しかし、これを使用するには、結果の配列を事前に割り当てできるように、`map_fnc`の`result_type`を指定する必要があります。
