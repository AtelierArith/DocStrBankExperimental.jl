```
RuntimeDependency(dep::Union{PackageSpec,String}; compat::String, platforms::Vector{<:AbstractPlatform}, top_level::Bool=false)
```

生成されたJLLパッケージの依存関係としてのみリストされるバイナリ依存関係を定義しますが、そのアーティファクトはビルド中にプレフィックスにインストールされません。`dep`引数は、JLLパッケージの名前を持つ文字列または`Pkg.PackageSpec`のいずれかであることができます。

オプションのキーワード引数`compat`は、生成されたJuliaパッケージの`Project.toml`で使用するための文字列を指定するために使用できます。

オプションのキーワード引数`platforms`は、依存関係が使用されるプラットフォームを示す`AbstractPlatform`のベクターです。デフォルトでは`platforms=[AnyPlatform()]`であり、これは依存関係がすべてのプラットフォームと互換性があることを意味します。

オプションのキーワード引数`top_level`は、依存関係が生成されたJLLパッケージのトップレベルでのみ使用されるべきか、各プラットフォーム固有のラッパー内で使用されるべきかを指定します。`top_level=true`を使用することは、プラットフォームの拡張に必要なパッケージ（例：`MPIPreferences.jl`）に便利です。
