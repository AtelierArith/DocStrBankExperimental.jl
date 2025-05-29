```
IKinSpace(Slist, M, T, thetalist0, eomg, ev)
```

空間フレームでの逆運動学をオープンチェーンロボットに対して計算します。

# 例

```jldoctest; setup = :(using ModernRoboticsBook)
julia> Slist = [  0  0  1  4  0  0   ;
                  0  0  0  0  1  0   ;
                  0  0 -1 -6  0 -0.1 ]';

julia> M = [ -1  0  0  0 ;
              0  1  0  6 ;
              0  0 -1  2 ;
              0  0  0  1 ];

julia> T = [ 0  1  0     -5 ;
             1  0  0      4 ;
             0  0 -1 1.6858 ;
             0  0  0      1 ];

julia> thetalist0 = [1.5, 2.5, 3];

julia> eomg, ev = 0.01, 0.001;

julia> IKinSpace(Slist, M, T, thetalist0, eomg, ev)
([1.5707378296567203, 2.999663844672524, 3.141534199856583], true)
```
