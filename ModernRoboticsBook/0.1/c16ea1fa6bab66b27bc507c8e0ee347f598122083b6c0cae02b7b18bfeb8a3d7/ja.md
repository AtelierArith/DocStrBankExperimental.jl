```
FKinBody(M, Blist, thetalist)
```

オープンチェーンロボットのボディフレームにおける前向き運動学を計算します。

# 例

```jldoctest; setup = :(using ModernRoboticsBook)
julia> M = [ -1  0  0  0 ;
              0  1  0  6 ;
              0  0 -1  2 ;
              0  0  0  1 ];

julia> Blist = [  0  0 -1  2  0  0   ;
                  0  0  0  0  1  0   ;
                  0  0  1  0  0  0.1 ]';

julia> thetalist = [ π/2, 3, π ];

julia> FKinBody(M, Blist, thetalist)
4×4 Matrix{Float64}:
 -1.14424e-17  1.0           0.0  -5.0    
  1.0          1.14424e-17   0.0   4.0    
  0.0          0.0          -1.0   1.68584
  0.0          0.0           0.0   1.0    
```
