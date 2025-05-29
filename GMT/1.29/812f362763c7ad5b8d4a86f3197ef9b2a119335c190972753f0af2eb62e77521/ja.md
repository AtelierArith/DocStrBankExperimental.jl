```
isclockwise(poly::Matrix{<:AbstractFloat}, view=(0.0,0.0,1.0)) -> Bool
```

`poly`が`view`方向から見たときに時計回りであればtrueを返します。

### 例

```julia
poly = [0.0 0.0 0.0; 0.0 0.0 1.0; 0.0 1.0 1.0; 0.0 1.0 0.0; 0.0 0.0 0.0]
isclockwise(poly, (1.0,0.1,0.0))
```
