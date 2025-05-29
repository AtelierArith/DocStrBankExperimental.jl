```
crystalsystem(Rs::DirectBasis{D})  -->  String
crystalsystem(Gs::ReciprocalBasis{D})  -->  String
```

`DirectBasis` `Rs`を持つ点格子の結晶系を決定します。これは、国際結晶学表に定義された従来の設定選択を仮定します[^ITA6]。

関連する逆点格子のために`ReciprocalBasis` `Gs`が提供されている場合、結晶系はまず直接格子に変換することによって決定されます。

2Dには4つの結晶系があり、3Dには7つの結晶系があります（[^^ITA5]のセクション2.1.2(iii)を参照）：

| `D`    |  系統 |                     条件 |          自由パラメータ |
|:------ | ---:| ----------------------:| ----------------:|
| **1D** |  線形 |                     なし |                a |
| **2D** | 正方形 |            a=b & γ=90° |                a |
|        | 長方形 |                  γ=90° |              a,b |
|        | 六角形 |           a=b & γ=120° |                a |
|        |  斜方 |                     なし |            a,b,γ |
| **3D** |  立方 |      a=b=c & α=β=γ=90° |                a |
|        |  六方 | a=b & α=β=90° & γ=120° |              a,c |
|        |  三方 | a=b & α=β=90° & γ=120° | a,c (a,α for hR) |
|        |  四方 |        a=b & α=β=γ=90° |              a,c |
|        | 正方晶 |              α=β=γ=90° |            a,b,c |
|        |  単斜 |                α=γ=90° |      a,b,c,β≥90° |
|        |  三斜 |                     なし |      a,b,c,α,β,γ |

`Rs`は従来の基底ベクトルのセットを指定する必要があります。すなわち、一般的に原始的ではありません。原始的な基底ベクトルの場合、結晶系は2Dで5つのブラヴェタイプ、3Dで14にさらに細分化できます（[`bravaistype`](@ref)を参照）。

[^ITA6]: M.I. Aroyo, International Tables of Crystallography, Vol. A, 6th ed. (2016): Tables      3.1.2.1 and 3.1.2.2 (または[^ITA5]のTables 2.1.2.1, 9.1.7.1, and 9.1.7.2)。

[^ITA5]: T. Hahn, International Tables of Crystallography, Vol. A, 5th ed. (2005).
