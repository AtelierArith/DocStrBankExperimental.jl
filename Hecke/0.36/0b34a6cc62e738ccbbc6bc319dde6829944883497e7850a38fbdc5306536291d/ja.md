```
TorQuadModule
```

# 例

```jldoctest
julia> A = matrix(ZZ, [[2,0,0,-1],[0,2,0,-1],[0,0,2,-1],[-1,-1,-1,2]]);

julia> L = integer_lattice(gram = A);

julia> T = Hecke.discriminant_group(L)
有限二次モジュール
  整数環上
アーベル群: (Z/2)^2
双線形値モジュール: Q/Z
二次値モジュール: Q/2Z
グラム行列二次形式:
[   1   1//2]
[1//2      1]
```

私たちは、トーション二次モジュールをフルランクのサブラティスによる$\mathbb{Z}$-ラティスの商として表現します。

それらは、アーベル群`A`への射影`p : M -> A`と共に$\mathbb{Z}$-ラティス`M`として保存されます。`A`の双線形構造は`p`を介して誘導され、すなわち`<a, b> = <p^-1(a), p^-1(a)>`であり、値は$\mathbb{Q}/n\mathbb{Z}$に属し、ここで$n$はモジュラスであり、`p`の核に依存します。

Aの要素は基本的に基礎となるアーベル群の要素です。`M`と`A`の間を移動するために、`lift`関数`lift : M -> A`と強制変換`A(m)`を使用します。

# 例

```jldoctest
julia> R = rescale(root_lattice(:D,4),2);

julia> D = discriminant_group(R);

julia> A = abelian_group(D)
(Z/2)^2 x (Z/4)^2

julia> d = D[1]
有限二次モジュールの要素: (Z/2)^2 x (Z/4)^2 -> Q/2Z
成分 [1 0 0 0]

julia> d == D(A(d))
true

julia> lift(d)
4-element Vector{QQFieldElem}:
 1
 1
 3//2
 1
```

注: $\mathbb{Z}$-ラティスの要素が存在しないため、私たちは`M`の要素を周囲のベクトル空間の要素として考えます。したがって、もし`v::Vector`がそのような要素であれば、`M`の基底に関する座標は`solve(basis_matrix(M), v; side = :left)`によって与えられます。
