# BestieTemplate.jl

このパッケージは、Juliaパッケージ用のコピー テンプレートと、それをJuliaから使用するための基本的なユーザー インターフェイスを定義します。

主な関数は、[`generate`](@ref)、[`apply`](@ref)、および[`update`](@ref)です。

BestieTemplateを使用して新しいパッケージを作成するには、次のコマンドを実行します。

```julia
julia> BestieTemplate.generate("path/to/YourNewPackage.jl")
```

既存のパッケージにテンプレートを適用するには、次のコマンドを実行します。

```julia
julia> BestieTemplate.apply("path/to/YourExistingPackage.jl")
```

ドキュメントを確認してください: https://JuliaBesties.github.io/BestieTemplate.jl
