# 集合体高斯求积运算模组

## 简介

本模组用于支持集合体高斯求积运算，提供高效的数值积分方法。

## 安装

使用以下命令安装模组：

```julia
using Pkg
Pkg.add("GaussianQuadrature")
```

## 使用示例

以下是如何使用该模组进行高斯求积运算的示例：

```julia
using GaussianQuadrature

# 定义被积函数
f(x) = exp(-x^2)

# 计算积分
result = gauss_quadrature(f, -Inf, Inf)
println("积分结果: ", result)
```

## 函数说明

### `gauss_quadrature(f, a, b)`

  * **参数**:

      * `f`: 被积函数
      * `a`: 积分下限
      * `b`: 积分上限
  * **返回**: 积分结果

## 参考文献

  * [高斯求积法](https://en.wikipedia.org/wiki/Gaussian_quadrature)
