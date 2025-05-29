Prefixes(prefixes::Dict{T,PrefixType}=Dict{String,PrefixType}(); prefix_file::Union{String,Nothing}=nothing, lang::Union{String,Nothing}="en") where {T<:AbstractString}

`Prefixes`を構築します。

# 引数

  * `prefixes::Dict{<:AbstractString,PrefixType}=Dict{T,PrefixType}()`: オプション。ノンブレイキングプレフィックスの辞書。
  * `prefix_file::Union{String,Nothing}=nothing`: オプション。提供された`prefixes`に追加するノンブレイキングプレフィックスを含むファイルへのパス。
  * `lang::AbstractString="en"`: オプション。`prefixes`に追加されるノンブレイキングプレフィックスの言語（利用可能な言語については`?SUPPORTED_LANG`を参照）。
