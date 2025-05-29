```
named_ss(sys::ExtendedStateSpace;       kwargs...)
named_ss(sys::ExtendedStateSpace, name; kwargs...)
```

ExtendedStateSpaceに名前を付けます。信号`z,y,w,u`および状態`x`に特定の名前が提供されていない場合、名前は自動的に生成されます。

# 引数:

  * `name`: 自動生成されたすべての名前に追加するプレフィックス。
  * `x`
  * `u`
  * `y`
  * `w`
  * `z`
