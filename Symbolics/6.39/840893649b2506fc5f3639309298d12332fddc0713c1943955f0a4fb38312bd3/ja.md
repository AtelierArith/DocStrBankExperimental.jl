```
ticksInState()
ticksInState(state)
```

有限状態機械において、状態で費やされたティックの数を取得します。

囲まれた状態で費やされたティックの数を照会するために引数なしのメソッドが使用されます。すなわち、

```julia
@mtkmodel FSM begin
    ...
    @equations begin
        var(k+1) ~ ticksInState() >= 2 ? 0.0 : var(k)
    end
end
```

別の状態でのティックの数を照会するためには、その状態を引数として渡します。

この演算子は、方程式と遷移条件の両方で使用できます。

他に [`timeInState`](@ref) と [`entry`](@ref) を参照してください。
