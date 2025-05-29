```
ScalarShape{T} <: AbstractScalarShape{T}
```

`ScalarShape`は、特定の型のスカラー値の形状を説明します。

コンストラクタ:

```
ScalarShape{T::Type}()
```

Tは、Unionの抽象型または特定の型である可能性があります。例えば、

```
ScalarShape{Real}()
ScalarShape{Integer}()
ScalarShape{Float32}()
ScalarShape{Complex}()
```

スカラー形状は、複素数値スカラーの形状のように、自由度の合計数（[`totalndof`](@ref)を参照）を1より大きく持つことがあります。

```
totalndof(ScalarShape{Real}()) == 1
totalndof(ScalarShape{Complex}()) == 2
```

[`AbstractValueShape`](@ref)のドキュメントも参照してください。
