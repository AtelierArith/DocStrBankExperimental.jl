```
unsynchronize!(o::AbstractObservable, o_sync::Union{AbstractObservable, Nothing} = nothing)
```

観測可能なものの同期を解除します。

### パラメータ

  * `o::AbstractObservable`: 同期を解除する観測可能なもの。
  * `o_sync::Union{AbstractObservable, Nothing}`: 同期を解除する対象の観測可能なもの。`nothing`（デフォルト）の場合、`o`からすべての双方向同期とすべての一方向同期を解除します。`o_sync`が渡された場合、`o`と`o_sync`の間のすべての同期を解除します。

### 例 1

```
o = Observable(0)
on(o -> println("o: $o"), o)
o1 = Observable(1)
on(o1 -> println("o1: $o1"), o)
o2 = Observable(2)
on(o2 -> println("o2: $o2"), o)
o3 = Observable(3)

synchronize!(o1, o)
synchronize!(o2, o)
synchronize!(o3, o, biderectional = false)

# o2のみの同期解除
unsynchronize!(o2)

# o3の同期解除の誤った方法、一方向のため
unsynchronize!(o3)

# o3の同期解除の正しい方法
unsynchronize!(o3, o)

# oからすべての同期を解除
unsynchronize!(o)
```
