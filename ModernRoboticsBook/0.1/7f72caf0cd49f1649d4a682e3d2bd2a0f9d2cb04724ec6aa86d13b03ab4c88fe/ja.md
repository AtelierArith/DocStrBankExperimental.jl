```
JacobianSpace(Slist, thetalist)
```

オープンチェーンロボットの空間ヤコビアンを計算します。

# 例

```jldoctest; setup = :(using ModernRoboticsBook)
julia> Slist = [0 0 1   0 0.2 0.2;
                1 0 0   2   0   3;
                0 1 0   0   2   1;
                1 0 0 0.2 0.3 0.4]';

julia> thetalist = [0.2, 1.1, 0.1, 1.2];

julia> JacobianSpace(Slist, thetalist)
6×4 Matrix{Float64}:
 0.0  0.980067  -0.0901156   0.957494 
 0.0  0.198669   0.444554    0.284876 
 1.0  0.0        0.891207   -0.0452841
 0.0  1.95219   -2.21635    -0.511615 
 0.2  0.436541  -2.43713     2.77536  
 0.2  2.96027    3.23573     2.22512  
```
