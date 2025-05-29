```
selection = select(addrs...)
```

指定されたアドレスのセットを含む選択を返します。

例:

```julia
selection = select(:x, "foo", :y => 1 => :z)
selection = select()
selection = select(:x => 1, :x => 2)
```
