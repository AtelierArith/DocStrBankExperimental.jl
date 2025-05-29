```
read_options(comonicon; kwargs...)
```

Comoniconビルドオプションを読み込みます。引数`comonicon`は次のいずれかです：

  * Comonicon CLIプロジェクトのモジュール。
  * `JuliaComonicon.toml`または`Comonicon.toml`を含むComonicon CLIプロジェクトへのパス。
  * `JuliaComonicon.toml`または`Comonicon.toml`という名前のComonicon CLIビルド構成ファイルへのパス。

場合によっては、TOMLファイルに書かれた構成を一時的に変更したいことがあります。例えば、ビルドテストを書くためなどです。この場合、対応するキーワード引数を使用して構成を変更できます。

[`Application`](@ref)および[`SysImg`](@ref)のキーワード引数は同じであるため、`read_options`では`filter_stdlibs`のようなキーは曖昧と見なされますが、特定の[`Application`](@ref)または[`SysImg`](@ref)オブジェクトを指定することで指定できます。例えば：

```julia
read_options(MyCLI; sysimg=SysImg(filter_stdlibs=false))
```

さらに[`Comonicon`](@ref)、[`Install`](@ref)、[`SysImg`](@ref)、[`Application`](@ref)、[`Download`](@ref)、[`Precompile`](@ref)も参照してください。
