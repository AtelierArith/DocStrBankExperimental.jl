```
HostBuildDependency(dep::Union{PackageSpec,String}; platforms)
```

パッケージをビルドするためにのみ必要なバイナリ依存関係を定義します。 [`BuildDependency`](@ref)とは異なり、ホストプラットフォーム用のアーティファクトがインストールされ、ターゲットプラットフォーム用のものはインストールされません。

`dep` 引数は、JLLパッケージの名前を持つ文字列または `Pkg.PackageSpec` のいずれかです。

オプションのキーワード引数 `platforms` は、依存関係が使用されるプラットフォームを示す `AbstractPlatform` のベクターです。 デフォルトでは `platforms=[AnyPlatform()]` となっており、依存関係がすべてのプラットフォームと互換性があることを意味します。
