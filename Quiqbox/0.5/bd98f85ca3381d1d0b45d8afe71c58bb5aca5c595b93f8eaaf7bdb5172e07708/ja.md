```
getParams(pbc::ParamBox, symbol::Union{Symbol, Missing}=missing) -> 
Union{ParamBox, Nothing}

getParams(pbc::ParameterizedContainer, symbol::Union{Symbol, Missing}=missing) -> 
AbstractVector{<:ParamBox}

getParams(pbc::Union{AbstractArray{<:T}, Tuple{T, Vararg{T}}}, 
          symbol::Union{Symbol, Missing}=missing) where {T<:QuiqboxContainer} -> 
AbstractVector{<:ParamBox}
```

入力コンテナに格納されているパラメータを返します。`symbol`が`missing`に設定されている場合、すべてのパラメータを返します。`symbol`がパラメータに関連付けられた`Symbol`に設定されている場合、例えば`:α₁`のように、関数は`pb::`[`ParamBox`](@ref)の中で`[`indVarOf`](@ref)`(pb)[begin] == :α₁`に一致するものを探します。`symbol`が添字のない`Symbol`に設定されている場合、例えば`:α`のように、関数は`string(indVarOf(pb)[begin])`が`'α'`を含むすべての`pb`に一致させます。最初の引数がコレクションである場合、そのエントリは`ParamBox`コンテナでなければなりません。
