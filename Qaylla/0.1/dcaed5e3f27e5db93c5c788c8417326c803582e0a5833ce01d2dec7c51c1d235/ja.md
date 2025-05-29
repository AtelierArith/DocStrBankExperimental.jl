```
cubic_splines(x_data,y_data)::Function
```

三次スプライン補間多項式を計算します

## 引数

  * `x_data`: i=1,2...n の xᵢ 値
  * `y_data`: i=1,2...n の f(xᵢ) 値

## 戻り値

  * `p::Function`: 三次スプライン補間多項式

## 例

```jldoctest
using Qaylla

x=0:pi/4:3*pi
y=sin.(x)
p=cubic_splines(x,y)
p(2.5)

# 出力

0.59842733419271

```
