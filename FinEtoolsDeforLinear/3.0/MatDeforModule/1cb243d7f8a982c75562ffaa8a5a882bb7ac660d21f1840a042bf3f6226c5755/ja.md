```
tens4symmtto6x6t!(M::Matrix{T}, ST::Array{T, 4}) where {T}
```

対称4次テンソルを6 x 6行列に変換します。

!!! 注 この順序は、応力（またはひずみ）テンソルの成分の配置に対応し、対称的で三次元の6成分ベクトルに変換されます。

# 例

```
J=tens4_ijkl(eye(3),eye(3))
トレースを生成します:
T=rand(3); 
sum(diag(T))*eye(3)
t= tens4_dot_2(J,T)
M= tens4_symm_to_6(ST)
```
