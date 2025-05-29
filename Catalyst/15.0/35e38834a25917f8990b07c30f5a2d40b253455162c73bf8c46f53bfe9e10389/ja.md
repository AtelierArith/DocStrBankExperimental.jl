isautonomous(rs::ReactionSystem)

システムが自律的であるかどうかをチェックします（すなわち、速度や方程式が独立変数に依存しない）。例：

```julia
rs1 = @reaction_system
    (p,d), 0 <--> X
end
isautonomous(rs1) # `true`を返します。

rs2 = @reaction_system
    (p/t,d), 0 <--> X
end
isautonomous(rs2) # `false`を返します。
```
