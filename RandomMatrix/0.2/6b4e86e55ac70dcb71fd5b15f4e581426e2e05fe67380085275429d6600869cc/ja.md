```julia
randUnitary(n::Int)
```

  * n×nのランダムユニタリ行列を生成します
  * `rand(Haar(2,n))`と同等であり、[`Haar`](@ref)および[`CUE`](@ref)を参照してください
  * 直交行列の場合は、`randOrthogonal`または`rand(Haar(1,n))`を使用してください
  * アルゴリズムについては、[How to Generate Random Matrices from the Classical Compact Groups](http://www.ams.org/notices/200705/fea-mezzadri-web.pdf)を参照してください

# 例

3×3のランダムユニタリ行列を生成します 

```julia
randUnitary(3)

3×3 Matrix{ComplexF64}:
 -0.149398+0.0572715im  -0.0935861+0.629201im  -0.257255-0.709625im
  0.337035-0.342606im     -0.36366+0.599236im  -0.100838+0.517231im
  -0.17097+0.845103im   -0.0767105+0.313259im   0.247081+0.3025im
```
