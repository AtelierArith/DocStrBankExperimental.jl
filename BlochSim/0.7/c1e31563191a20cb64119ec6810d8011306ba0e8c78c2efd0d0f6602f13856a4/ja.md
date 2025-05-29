```
applydynamics!(spin, BtoM, A, [B])
```

与えられたスピンにダイナミクスを適用し、スピンの磁化ベクトルを上書きします。`BtoM`は中間結果を格納するために使用され（したがって上書きされます）。

# 例

```jldoctest
julia> s = Spin(1, 1000, 100, 3.75); s.M
磁化ベクトルの型は Float64:
 Mx = 0.0
 My = 0.0
 Mz = 1.0

julia> BtoM = Magnetization();

julia> (A,) = excite(s, InstantaneousRF(π/2)); applydynamics!(s, BtoM, A); s.M
磁化ベクトルの型は Float64:
 Mx = 1.0
 My = 0.0
 Mz = 6.123233995736766e-17

julia> (A, B) = freeprecess(s, 100); applydynamics!(s, BtoM, A, B); s.M
磁化ベクトルの型は Float64:
 Mx = -0.2601300475114444
 My = -0.2601300475114445
 Mz = 0.09516258196404054
```
