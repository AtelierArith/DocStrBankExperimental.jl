```
yticks(sp::Subplot)
```

は、サブプロット `sp` の y 軸の目盛りを返します。

目盛りは値とラベルのタプルとして返されることに注意してください：

```jldoctest
julia> sp = plot(1:5, yticks=[1,2]).subplots[1]
Subplot{1}

julia> yticks(sp)
([1.0, 2.0], ["1", "2"])
```
