```
LazyBranch(f::ROOTFile, branch)
```

指定されたブランチのアクセサを構築し、`BA[idx]` または `BA[1:20]` が型安定になるようにします。また、メモリフットプリントは単一のバスケット（通常は1MB未満）です。反復処理やマッピングも可能です。具体的な `Vector` が必要な場合は、単に `collect()` して LazyBranch を取得してください。

# 例

```julia
julia> rf = ROOTFile("./test/samples/tree_with_large_array.root");

julia> b = rf["t1/int32_array"];

julia> ab = UnROOT.LazyBranch(rf, b);

julia> for entry in ab
           @show entry
           break
       end
entry = 0

julia> ab[begin:end]
0
1
...
```
