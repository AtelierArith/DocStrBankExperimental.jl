```
combine!(A, B, A1, B1, A2, B2)
combine!(A, A1, A2)
```

スピンの動力学を記述する行列とベクトルを1つの行列と1つのベクトルに結合し、`A`と`B`を上書きします。`A1`と`B1`によって記述される動力学が最初に適用され、その後に`A2`と`B2`によって記述される動力学が適用されます。言い換えれば、`A = A2 * A1`および`B = A2 * B1 + B2`です。

# 例

```jldoctest
julia> s = Spin(1, 1000, 100, 3.75);

julia> A = BlochMatrix(); B = Magnetization();

julia> (A1, B1) = excite(s, InstantaneousRF(π/2));

julia> (A2, B2) = freeprecess(s, 100);

julia> combine!(A, B, A1, B1, A2, B2); A * s.M + B
磁化ベクトルの型は Float64:
 Mx = -0.2601300475114444
 My = -0.2601300475114445
 Mz = 0.09516258196404054
```
