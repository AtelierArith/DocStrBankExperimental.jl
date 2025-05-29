```
timeInState()
timeInState(state)
```

有限状態機械における状態に費やした時間（秒単位）を取得します。

囲まれた状態に費やした時間を照会するために使用される場合、引数なしのメソッドが使用されます。すなわち、

```julia
@mtkmodel FSM begin
    ...
    @equations begin
        var(k+1) ~ timeInState() >= 2 ? 0.0 : var(k)
    end
end
```

別の状態の滞在時間を照会するために使用される場合、その状態が引数として渡されます。

この演算子は、方程式と遷移条件の両方で使用できます。

[`ticksInState`](@ref) および [`entry`](@ref) も参照してください。
