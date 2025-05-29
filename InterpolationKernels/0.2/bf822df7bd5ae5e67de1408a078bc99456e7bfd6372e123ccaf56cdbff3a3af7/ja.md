```
CatmullRomSplinePrime{T}()
```

は、浮動小数点型 `T` の Catmull-Rom 補間カーネルの 1 次導関数であるカーネルインスタンスを生成します（詳細は [`CatmullRomSpline`](@ref) を参照）。`T` が省略された場合、`Float64` であると仮定されます。

Catmull-Rom 補間カーネルの 1 次導関数は次のように与えられます：

```
ker′(x) = ((9/2)*|x| - 5)*x                      もし a = |x| ≤ 1
          (5 - (3/2)*|x|)*x - 4*sign(x)          もし 1 ≤ |x| ≤ 2
          0                                      もし |x| ≥ 2
```
