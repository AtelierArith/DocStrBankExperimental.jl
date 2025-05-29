```
NewtonDescent(; linsolve = nothing)
```

降下方向を計算します。$J δu = -fu$。非正方形ヤコビ行列の問題では、これは一般的にガウス-ニュートン降下法と呼ばれます。

関連情報としては、[`Dogleg`](@ref)、[`SteepestDescent`](@ref)、[`DampedNewtonDescent`](@ref)があります。
