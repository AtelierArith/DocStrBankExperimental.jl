`FrameworkProduct`は、macOSフレームワークをカプセル化した[`Product`](@ref)です。現時点では主に[`LibraryProduct`](@ref)として振る舞いますが、異なるタイプです。これは、macOSではフレームワークとしてライブラリが提供され、他のプラットフォームでは通常のライブラリとして提供されるクロスプラットフォームビルドの場合、BinaryBuilderの`build_tarballs`を2回呼び出す必要があることを意味します。1回は`LibraryProduct`とすべての非macOSプラットフォーム用、もう1回は`FrameworkProduct`と`MacOS`プラットフォーム用です。

---

```
FrameworkProduct(fwnames, varname::Symbol)
```

プレフィックス内にあるフレームワークを指すmacOS `FrameworkProduct`を宣言します。名前には`fwname`が`.framework`を付加したものが含まれます。例えば、`fwname`が`QtCore`に等しい場合、次のパスで満たされます。

```
lib/QtCore.framework
```
