```
lagrange(x,y)::Function
```

ラグランジュ補間多項式を計算します

## 引数

  * `x::Vector{Number}`: i=1,2...n の xᵢ 値
  * `y::Vector{Number}`: i=1,2...n の f(xᵢ) 値

## 戻り値

  * `p::Function`: ラグランジュ補間多項式

## 例

```jldoctest
using Qaylla

x=0:0.5:3
y=exp.(x)
p=newton(x,y)
p(2.5)

# 出力

12.182493960703471
```
