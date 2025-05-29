```
repackva!(fi::FuncInfo, varid::Union{SlotNumber, Int}, vaid::Union{SlotNumber, Int}, indices::Vector{Integer}) = begin
    # 新しい vararg (`vaid`) を与えられた場合、`indices` で要素を抽出し、タプルとしてパックして古い vararg (`varid`) に割り当てます。
    old_vararg = (vaid[indices]...)
    varid = old_vararg
end
```
