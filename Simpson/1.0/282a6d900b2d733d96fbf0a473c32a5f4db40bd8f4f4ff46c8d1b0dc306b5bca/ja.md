```
simpson(y, x, dx, even)
```

Simpson.jlは、サンプルを使用してy(x)を積分するためのJuliaパッケージです。

xがnothingの場合、dxの間隔が仮定されます。

サンプルの数が偶数Nの場合、区間の数は奇数(N-1)ですが、シンプソンのルールでは偶数の区間が必要です。パラメータ'even'は、これがどのように処理されるかを制御します。

このコードはSciPy v1.7.1に基づいています: https://github.com/scipy/scipy/blob/v1.7.1/scipy/integrate/_quadrature.py

# 引数

  * `y::Vector{<:Real}` : 積分されるベクトル。
  * `x::Union{Vector{<:Real}, Nothing}=nothing`, オプション : `y`がサンプリングされるベクトル。
  * `dx::Real`, オプション : `x`の軸に沿った積分点の間隔。`x`がnothingの場合のみ使用されます。デフォルトは1.0です。
  * `even::Symbol[:avg, :first, :last]`, オプション   :avg、デフォルト : 2つの結果の平均を取ります：

    1. 最初のN-2区間に対して台形法を使用し、最後の区間に対して
    2. 最後のN-2区間に対して台形法を使用し、最初の区間に対して。

    :first : 最初のN-2区間に対してシンプソンのルールを使用し、最後の区間に対して台形法を使用します。   :last : 最後のN-2区間に対してシンプソンのルールを使用し、最初の区間に対して台形法を使用します。

# 注意事項

等間隔のサンプルが奇数の場合、関数が3次以下の多項式であれば結果は正確です。サンプルが等間隔でない場合、結果は関数が2次以下の多項式である場合にのみ正確です。

# 例

```
julia> x = 0:9
julia> y = 0:9
julia> simpson(x, y)
40.5

julia> y = x .^ 3
julia> simpson(y, x)
1642.5

julia> simpson(y, x, even=:first)
1644.5

julia> simpson(y, x, even=:last)
1640.5
```
