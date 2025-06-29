```
root_lattice_recognition(L::ZZLat)
```

`L`のルート部分格子のADEタイプを返します。

ルート部分格子は、平方長が$1$および$2$のベクトルによって張られる格子です。階数1で行列式が$1$の奇数格子は`(:I, 1)`で表されます。

入力:

`L` – 定義された整数$\mathbb{Z}$-格子。

出力:

2つのリスト、最初のリストにはADEタイプが含まれ、2番目のリストには不可約ルート部分格子が含まれます。

より認識しやすいグラム行列を使用するには[`root_lattice_recognition_fundamental`](@ref)を参照してください。

# 例

```jldoctest
julia> L = integer_lattice(; gram=ZZ[4  0 0  0 3  0 3  0;
                                     0 16 8 12 2 12 6 10;
                                     0  8 8  6 2  8 4  5;
                                     0 12 6 10 2  9 5  8;
                                     3  2 2  2 4  2 4  2;
                                     0 12 8  9 2 12 6  9;
                                     3  6 4  5 4  6 6  5;
                                     0 10 5  8 2  9 5  8])
階数8、次数8の整数格子
グラム行列
[4    0   0    0   3    0   3    0]
[0   16   8   12   2   12   6   10]
[0    8   8    6   2    8   4    5]
[0   12   6   10   2    9   5    8]
[3    2   2    2   4    2   4    2]
[0   12   8    9   2   12   6    9]
[3    6   4    5   4   6   6    5]
[0   10   5    8   2   9   5    8]

julia> R = root_lattice_recognition(L)
([(:A, 1), (:D, 6)], ZZLat[階数1、次数8の整数格子, 階数6、次数8の整数格子])

julia> L = integer_lattice(; gram = QQ[1 0 0  0;
                                       0 9 3  3;
                                       0 3 2  1;
                                       0 3 1 11])
階数4、次数4の整数格子
グラム行列
[1   0   0    0]
[0   9   3    3]
[0   3   2    1]
[0   3   1   11]

julia> root_lattice_recognition(L)
([(:A, 1), (:I, 1)], ZZLat[階数1、次数4の整数格子, 階数1、次数4の整数格子])
```
