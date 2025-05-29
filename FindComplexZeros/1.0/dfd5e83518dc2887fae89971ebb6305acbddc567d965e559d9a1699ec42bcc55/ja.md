```
findZerosWithSubdivision(upper_left, lower_right, f::Function, err=0.01, increment = err/100, dif=0.5)
```

与えられた長方形領域内の関数のゼロの位置を見つける

結果の各行には、ゼロを含む長方形ボックスの左上隅と右下隅が含まれます

# 引数

  * `upper_left`: 長方形領域の左上隅の複素数
  * `lower_right`: 長方形領域の右下隅の複素数
  * `f::Function`: 関数
  * `err=0.001`: 各ゼロの位置の誤差
  * `increment=err/100`: `countZeros`関数のステップサイズ
  * `dif=0.5`: `countZeros`関数による評価の2つの連続点での$arg(f(z))$の差が`2pi-dif`より大きい場合、ジャンプポイントが登録されます

# 例

```julia-repl
julia> function exp_sum(x)
    return (1+im)*exp(x) + (3.5+2*im) + (3-im)*exp(-x)
end
exp_sum (generic function with 1 method)

julia> findZerosWithSubdivision(-10 + 10im, 10 - 10im, exp_sum, 0.01)
7-element Vector{Tuple{Any, Any}}:
 (0.859375 - 3.0859375im, 0.869140625 - 3.095703125im)
 (0.859375 - 9.375im, 0.869140625 - 9.384765]625im)
 (0.859375 + 9.47265625im, 0.869140625 + 9.462890625im)
 (0.859375 + 3.193359375im, 0.869140625 + 3.18359375im)
 (-0.068359375 + 1.9921875im, -0.05859375 + 1.982421875im)
 (-0.068359375 + 8.271484375im, -0.05859375 + 8.26171875im)
 (-0.068359375 - 4.287109375im, -0.05859375 - 4.296875im)
```
