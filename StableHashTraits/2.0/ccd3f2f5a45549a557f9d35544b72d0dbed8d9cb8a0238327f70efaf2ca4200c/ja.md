```
stable_hash(x, context; alg=sha256)
stable_hash(x; alg=sha256, version)
```

与えられたオブジェクトの安定したハッシュを作成します。コンテキストが同じである限り、このハッシュはjuliaのバージョンを超えて変更されないことを意図しています。組み込みのコンテキストはHashVersion{N}であり、`version`を指定すると、これは明示的に`HashVersion{version}`を渡すことと同等です。

バージョンは明示的に指定する必要があります。将来のリリースで新しいハッシュバージョンが提供された場合でも、結果は*変更されません*。

ハッシュの計算方法をカスタマイズするには、[`transformer`](@ref)を使用します。

使用するハッシュアルゴリズムを変更するには、`alg`に異なる関数を渡します。これは、`SHA`からの任意の`sha`関連関数または`hash(x::AbstractArray{UInt8}, [old_hash])`の形式の任意の関数を受け入れます。

`context`の値は、[`transformer`](@ref)への2番目の引数として渡されます。詳細については[Using Contexts](@ref)を参照してください。

## 関連項目

[`transformer`](@ref) ```
