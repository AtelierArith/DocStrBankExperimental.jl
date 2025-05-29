```
compute_angle_δᵥ(mbqc, qubits, ϕ, Sx, Sz)
```

与えられたMBQC、キュービット、ϕ、Sx、およびSzのための角度δᵥを計算します。

# 引数

  * `mbqc`: MBQCオブジェクト。
  * `qubits`: キュービットオブジェクト、`NoInputQubits`または`InputQubits`のいずれか。
  * `ϕ`: 角度ϕ。
  * `Sx`: Sxの値。
  * `Sz`: Szの値。

# 戻り値

  * 更新された角度δᵥ。

# 例

```julia
julia> compute_angle_δᵥ(MBQC(), NoInputQubits(), 0, 0, [0, 0, 0])
0
```
