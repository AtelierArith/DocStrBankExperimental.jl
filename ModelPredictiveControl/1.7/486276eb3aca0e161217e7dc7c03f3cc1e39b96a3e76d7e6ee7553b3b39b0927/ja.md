```
LinModel(sys::TransferFunction[, Ts]; i_u=1:size(sys,2), i_d=Int[])
```

`sys`が伝達関数であるとき、最小実現状態空間に変換します。

`sys`は、連続時間の場合は$\frac{\mathbf{y}(s)}{\mathbf{z}(s)}$、離散時間の場合は$\frac{\mathbf{y}(z)}{\mathbf{z}(z)}$に等しいです。

詳細は[`tf`](@extref ControlSystemsBase.tf)を参照してください。

# 例

```jldoctest
julia> model = LinModel([tf(3, [30, 1]) tf(-2, [5, 1])], 0.5, i_d=[2])
LinModel with a sample time Ts = 0.5 s and:
 1 manipulated inputs u
 2 states x
 1 outputs y
 1 measured disturbances d
```
