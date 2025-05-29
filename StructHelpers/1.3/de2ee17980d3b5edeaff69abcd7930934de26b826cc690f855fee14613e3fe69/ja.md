```
@batteries T [options]
```

型 `T` のためにいくつかのメソッドを自動的に導出します。

# 例

```julia
struct S
    a
    b
end

@batteries S
@batteries S hash=false # `Base.hash` をオーバーロードしない
@batteries S kwconstructor=true # キーワードコンストラクタを追加
```

サポートされているオプションとデフォルトは次のとおりです：

  * **eq** = true:

`Base.(==)` を構造的に定義します。

  * **isequal** = true:

`Base.isequal` を構造的に定義します。

  * **hash** = true:

`Base.hash` を構造的に定義します。

  * **kwconstructor** = false:

キーワードコンストラクタを追加します。

  * **selfconstructor** = true:

`T(self::T) = self` の形式のコンストラクタを追加します。

  * **kwshow** = false:

各フィールドの名前が印刷されるように `Base.show` をオーバーロードします。

  * **getproperties** = true:

`ConstructionBase.getproperties` をオーバーロードします。

  * **constructorof** = true:

`ConstructionBase.constructorof` をオーバーロードします。

  * **typesalt** = nothing:

`hash=true` の場合にのみ使用されます。この場合、`hash` は `typesalt` と `hash_eq_as(obj)` から純粋に計算されます。型 `T` はそれ以外では使用されません。これにより、異なるマシンや Julia バージョンで実行してもハッシュが一定に保たれる可能性が高くなります。

  * **StructTypes** = false:

`StructTypes.StructType` を `Struct()` にオーバーロードします。`StructTypes.jl` パッケージがインストールされている必要があります。

[`hash_eq_as`](@ref) も参照してください。
