```julia
macro pipeline(args...)
```

提供された式を連結する[`Pipeline`](@ref)を作成します。

例として、構文は次のようになります：

```julia
p = @pipeline Recenter() → Compress → Shrink(Fisher; threaded=false)
```

注意点：

  * 条件を区切る記号 → (エスケープ "\to") はオプションです。
  * このマクロにはエイリアス `@→` があります。
  * 上記の例のように、式はインスタンス化された条件、例えば `Recenter()`、またはその型、例えば `Compress` であり、その場合はその型のデフォルト条件が作成されます。

したがって、上記の例は次のように等価です：

```julia
    p = @→ Recenter() Compress() Shrink(Fisher; threaded=false)
```

条件はマクロによって呼び出すことはできません。したがって、変数を渡したい場合は、次のように書かないでください：

```julia
    R = Recenter()
    p = @→ R
```

代わりに次のように書いてください：

```julia
    R = Recenter()
    p = @→ eval(R)
```

**パイプラインを形成するための利用可能な条件**

[`Tikhonov`](@ref), [`Recenter`](@ref), [`Compress`](@ref), [`Equalize`](@ref), [`Shrink`](@ref)

**関連情報**: [`fit!`](@ref), [`transform!`](@ref)

**例**

```julia
using PosDefManifoldML, PosDefManifold

P=randP(3, 5)
pipeline = fit!(P, @→ Recenter → Compress)
```
