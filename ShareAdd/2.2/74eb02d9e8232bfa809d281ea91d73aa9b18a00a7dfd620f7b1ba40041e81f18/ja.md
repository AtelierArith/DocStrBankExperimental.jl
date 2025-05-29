```
update()
update(nm::AbstractString; warn_if_missing=false)
update(nm::Vector{<:AbstractString}; warn_if_missing=true)
update(env::AbstractString, pkgs::Union{AbstractString, Vector{<:AbstractString}}; warn_if_missing=true) 
update(env::EnvInfo, pkgs::Union{Nothing, S, Vector{S}} = Nothing; warn_if_missing=false) where S <: AbstractString
update(p::Pair{<:AbstractString, <:AbstractString}; warn_if_missing=false)
```

  * 引数なしで呼び出すと、すべての共有環境が更新されます。
  * 引数 `nm::String` が "@" で始まる単一の引数で呼び出すと、共有環境 `nm` が更新されます。
  * 引数 `nm::String` が "@" で始まらない単一の引数で呼び出すと、パッケージ `nm` が含まれるすべての共有環境で更新され、その下流の依存関係も更新されます。
  * 引数 `nm::Vector{String}` が単一の引数で呼び出すと、`nm` 内のパッケージおよび/または環境が更新されます。
  * 引数 `env` と `pkgs` の2つで呼び出すと、環境 `env` 内のパッケージ `pkgs` が更新されます。
  * 引数 `env => pkg` で呼び出すと、環境 `env` 内のパッケージ `pkg` が更新されます。

# kwarg

  * `warn_if_missing::Bool=true` - env または pkg が見つからない場合、警告を発行し、そうでなければエラーをスローします。

Julia バージョンがバージョン固有のマニフェストをサポートしている場合、更新のたびに各更新された環境にバージョン付きのマニフェストが作成されます。詳細は [`make_current_mnf`](@ref) を参照してください。

`nothing` を返します。

# 例

```julia-repl
julia> ShareAdd.update("@StatPackages")
julia> ShareAdd.update("@Foo" => "bar")
```

この関数は公開されており、エクスポートされていません。
