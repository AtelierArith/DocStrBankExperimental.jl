ステイビライザー、すなわち、可換な多量子ビットエルミートパウリ演算子のリスト。

インスタンスは、`S`カスタム文字列マクロを使用するか、他のステイビライザーの直和として作成できます。

!!! tip "ステイビライザーとデステイビライザー"
    多くの場合、[`MixedDestabilizer`](@ref)データ構造を使用する方が好ましいでしょう。これは、ランクやデステイビライザー演算子の追跡など、多くの有用な追加情報を持っています。`Stabilizer`は主に教育的な価値があり、特定のクリフォード操作のサブセットのわずかに高速なシミュレーションにも使用されます。


```jldoctest stabilizer
julia> s = S"XXX
             ZZI
             IZZ"
+ XXX
+ ZZ_
+ _ZZ

julia> s⊗s
+ XXX___
+ ZZ____
+ _ZZ___
+ ___XXX
+ ___ZZ_
+ ____ZZ
```

インデックスAPIがあり、`PauliOperator`のリストのように見えます。

```jldoctest stabilizer
julia> s[2]
+ ZZ_
```

パウリ演算子は、ステイビライザーに直接作用することができます。

```jldoctest stabilizer
julia> P"YYY" * s
- XXX
+ ZZ_
+ _ZZ
```

ステイビライザーを作成する方法はいくつかあります。

  * パウリ演算子のリストからステイビライザーを生成する

```jldoctest stabilizer
julia> Stabilizer([P"XX", P"ZZ"])
+ XX
+ ZZ
```

  * ブール行列からステイビライザーを生成する

```jldoctest stabilizer
julia> a = [true true; false false]; b = [false true; true true];

julia> Stabilizer(a, b)
+ XY
+ ZZ

julia> Stabilizer([0x0, 0x2], a, b)
+ XY
- ZZ
```

  * 空のステイビライザーを初期化し、インデックスを通じて埋める

```jldoctest stabilizer
julia> s = zero(Stabilizer, 2)
+ __
+ __

julia> s[1,1] = (true, false); s
+ X_
+ __
```

正しさの自動チェックはありません（すなわち、すべての行の独立性、すべての行の可換性、すべての行のエルミート性）。ランク（行の数）は、量子ビットの数（列の数）よりも少なくすることが許可されています：正準化、射影などはその場合でも機能し続けます。このライブラリは、`Stabilizer`データ構造を単に表として使用しています。これは将来のバージョンで適切に抽象化されるかもしれません。

関連情報: [`PauliOperator`](@ref), [`canonicalize!`](@ref)
