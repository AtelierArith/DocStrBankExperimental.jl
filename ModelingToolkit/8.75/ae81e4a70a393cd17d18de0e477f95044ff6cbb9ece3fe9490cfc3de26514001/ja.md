```
ShiftIndex
```

`ShiftIndex` 演算子は、信号にインデックスを付けて、シフトされた離散時間信号を取得することを可能にします。信号が連続時間の場合、シフトする前に信号がサンプリングされます。

# 例

```
julia> @variables t x(t);

julia> k = ShiftIndex(t, 0.1);

julia> x(k)      # シフトなし
x(t)

julia> x(k+1)    # シフト
Shift(t, 1)(x(t))
```
