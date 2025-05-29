```
RaySplitter(idxs, transmission, refraction [, newangular]; affect)
```

`RaySplitter` インスタンスを返し、レイの分割を行います。`idxs` は、この `RaySplitter` に対応する障害物のインデックスを持つ `Vector{Int}` です。

`transmission`、`refraction` および `newangular` は **関数** です。`φ` を入射角、`ω` を角速度、`pflag` を伝播フラグ（伝播前）とします。関数は以下のシグネチャを持ちます：

1. `transmission(φ, pflag, ω) -> T`、伝播確率。
2. `refraction(φ, pflag, ω) -> θ`、屈折角。この角度は *法線ベクトル* に対して相対的です。
3. `newangular(ω, pflag) -> newω`、伝播後の新しい角速度。

上記の3つの関数は **同じ規約** を使用します：引数 `pflag` は障害物が **伝播前** に持つものです。例えば、粒子が [`Antidot`](@ref) の外にあり（ここで `pflag = true`）、`Antidot` の内部に伝播されると（ここで `pflag` は `false` になります）、すべての3つの関数にはその2番目の引数（ブール値）が `true` として与えられます！

`affect` は関数であり、障害物 `i` で伝播が発生したときにビリヤードのどの障害物が影響を受けるかを示します（フィールド `pflag` を反転させるべき障害物）。デフォルトは `idxs = (i) -> i` であり、すなわち衝突している障害物のみが影響を受けます。多くの障害物に影響を与えたい場合は、`idxs = (i) -> SVector(2,3,5)` などと記述できます。この関数に渡すことができる `i` の値は、引数 `idxs` に与えられたものだけであることに注意してください！
