```
VersionNumber
```

セマンティックバージョニング（semver）の仕様に従ったバージョン番号タイプで、メジャー、マイナー、パッチの数値値で構成され、プレリリースおよびビルドのアルファベットと数字の注釈が続きます。

`VersionNumber` オブジェクトは、すべての標準比較演算子（`==`、`<`、`<=` など）で比較でき、その結果は semver ルールに従います。

また、セマンティックバージョン形式のリテラル文字列から `VersionNumber` オブジェクトを効率的に構築するための [`@v_str`](@ref)、Julia 自体の `VersionNumber` に関する [`VERSION`](@ref)、およびマニュアルの [Version Number Literals](@ref man-version-number-literals) も参照してください。

# 例

```jldoctest
julia> a = VersionNumber(1, 2, 3)
v"1.2.3"

julia> a >= v"1.2"
true

julia> b = VersionNumber("2.0.1-rc1")
v"2.0.1-rc1"

julia> b >= v"2.0.1"
false
```
