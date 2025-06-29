```
[`Frobenius` 行列](https://en.wikipedia.org/wiki/Frobenius_matrix)
```

フロベニウス行列またはガウス消去行列は次の形をしています。

```
[ 1 0 ...     0 ]
[ 0 1 ...     0 ]
[ .........     ]
[ ... 1 ...     ]
[ ... c1 1 ...  ]
[ ... c2 0 1 ...]
[ ............. ]
[ ... ck ...   1]
```

すなわち、1つの列に沿った非ゼロの下対角要素を持つ単位行列です。

この実装では、非ゼロ列の下対角要素は密なベクトルとして保存されるため、サイズは自動的に j+k と推測されます。ここで j は列インデックス、k は下対角要素の数です。

```jldoctest
julia> using SpecialMatrices

julia> F = Frobenius(3, 4:6) # 列 3 の下対角要素を指定
6×6 Frobenius{Int64}:
 1  0  0  0  0  0
 0  1  0  0  0  0
 0  0  1  0  0  0
 0  0  4  1  0  0
 0  0  5  0  1  0
 0  0  6  0  0  1

julia> inv(F) # 逆行列の特別な形
6×6 Frobenius{Int64}:
 1  0   0  0  0  0
 0  1   0  0  0  0
 0  0   1  0  0  0
 0  0  -4  1  0  0
 0  0  -5  0  1  0
 0  0  -6  0  0  1

julia> F*F # 同じ列に下対角要素がある場合、特別な形が保持される
6×6 Frobenius{Int64}:
 1  0   0  0  0  0
 0  1   0  0  0  0
 0  0   1  0  0  0
 0  0   8  1  0  0
 0  0  10  0  1  0
 0  0  12  0  0  1

julia> F*Frobenius(2, 2:5) # 行列に昇格
6×6 Matrix{Int64}:
 1   0  0  0  0  0
 0   1  0  0  0  0
 0   2  1  0  0  0
 0  11  4  1  0  0
 0  14  5  0  1  0
 0  17  6  0  0  1

julia> F * [10.0,20,30,40,50,60.0]
6要素のベクトル{Float64}:
  10.0
  20.0
  30.0
 160.0
 200.0
 240.0
```
