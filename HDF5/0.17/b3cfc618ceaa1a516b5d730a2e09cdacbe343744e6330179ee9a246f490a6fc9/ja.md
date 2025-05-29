```
h5open(f::Function, args...; pv...)
```

`h5open(args...; kwargs...)` の結果に関数 f を適用し、完了後に結果の `HDF5.File` を閉じます。例えば `do` ブロックを使った場合：

```
h5open("foo.h5","w") do h5
    h5["foo"]=[1,2,3]
end
```
