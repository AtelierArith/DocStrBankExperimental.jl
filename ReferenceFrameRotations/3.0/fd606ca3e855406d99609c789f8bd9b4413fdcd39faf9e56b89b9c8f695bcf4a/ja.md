```
Quaternion(q0::T0, q1::T1, q2::T2, q3::T3) where {T0, T1, T2, T3}
```

次のクォータニオンを作成します：

```
q0 + q1.i + q2.j + q3.k
```

ここで：

  * `q0` はクォータニオンの実部です。
  * `q1` はクォータニオンのベクトル部のX成分です。
  * `q2` はクォータニオンのベクトル部のY成分です。
  * `q3` はクォータニオンのベクトル部のZ成分です。

!!! note
    クォータニオン型は `T0`、`T1`、`T2`、および `T3` を昇格させることによって得られます。


# 例

```jldoctest
julia> Quaternion(1, 0, 0, 0)
Quaternion{Int64}:
  + 1 + 0⋅i + 0⋅j + 0⋅k

julia> Quaternion(1, 0, 0, 0.0)
Quaternion{Float64}:
  + 1.0 + 0.0⋅i + 0.0⋅j + 0.0⋅k
```

---

```
Quaternion(v::AbstractVector)
```

ベクトル `v` が3成分を持つ場合、実部が `0` で、ベクトル部または虚部がベクトル `v` の同じ成分を持つクォータニオンを作成します。言い換えれば：

```
q = 0 + v[1].i + v[2].j + v[3].k
```

そうでない場合、ベクトル `v` が4成分を持つ場合、入力ベクトルの要素に一致するクォータニオンを作成します：

```
q = v[1] + v[2].i + v[3].j + v[4].k
```

!!! note
    `v` の長さが3または4でない場合、エラーがスローされます。


# 例

```jldoctest
julia> Quaternion([0, cosd(45), sind(45)])
Quaternion{Float64}:
  + 0.0 + 0.0⋅i + 0.707107⋅j + 0.707107⋅k

julia> Quaternion([cosd(45), 0, sind(45), 0])
Quaternion{Float64}:
  + 0.707107 + 0.0⋅i + 0.707107⋅j + 0.0⋅k
```

---

```
Quaternion(r::Number, v::AbstractVector)
```

実部 `r` とベクトル部または虚部 `v` を持つクォータニオンを作成します：

```
r + v[1].i + v[2].j + v[3].k
```

!!! note
    クォータニオン型は `r` の型と `v` の要素の型を昇格させることによって得られます。


# 例

```jldoctest
julia> Quaternion(cosd(45), [0, sind(45), 0])
Quaternion{Float64}:
  + 0.707107 + 0.0⋅i + 0.707107⋅j + 0.0⋅k
```

---

```
Quaternion(u::UniformScaling{T}) where T
Quaternion{T}(u::UniformScaling) where T
Quaternion(u::UniformScaling, Q::Quaternion{T}) where T
```

クォータニオン `u.λ + 0.i + 0.j + 0.k` を作成します。

第三のシグネチャでクォータニオンが渡された場合、新しいクォータニオンは同じ型になります。

# 例

```jldoctest
julia> Quaternion(I)
Quaternion{Bool}:
  + true + false⋅i + false⋅j + false⋅k

julia> Quaternion(1.0I)
Quaternion{Float64}:
  + 1.0 + 0.0⋅i + 0.0⋅j + 0.0⋅k

julia> q = Quaternion{Float32}(I)
Quaternion{Float32}:
  + 1.0 + 0.0⋅i + 0.0⋅j + 0.0⋅k

julia> Quaternion(I, q)
Quaternion{Float32}:
  + 1.0 + 0.0⋅i + 0.0⋅j + 0.0⋅k
```
