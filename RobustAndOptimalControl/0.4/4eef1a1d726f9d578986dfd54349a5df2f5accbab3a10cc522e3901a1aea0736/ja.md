```
vec2sys(v::AbstractArray, ny::Int, nu::Int, ts = nothing)
```

パラメータから状態空間システムを作成します。

```julia
v = vec(sys) = [vec(sys.A); vec(sys.B); vec(sys.C); vec(sys.D)]
```

`vec(sys)`を使用して`v`を作成します。

これは、最適化などのためにベクトルに変換する際に便利です。

```@example
julia> sys  = ss(tf(1, [1, 1]))
StateSpace{Continuous, Float64}
A = 
 -1.0
B = 
 1.0
C = 
 1.0
D = 
 0.0

連続時間状態空間モデル

julia> v    = vec(sys)
4-element Vector{Float64}:
 -1.0
  1.0
  1.0
  0.0

julia> sys2 = vec2sys(v, sys.ny, sys.nu)
StateSpace{Continuous, Float64}
A = 
 -1.0
B = 
 1.0
C = 
 1.0
D = 
 0.0

連続時間状態空間モデル
```
