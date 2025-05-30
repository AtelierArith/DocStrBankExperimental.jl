```
FastaReader(f::Function, filename::AbstractString, [sequence_type::Type = String])
```

このコンストラクタの形式は、do-notationに便利です。すなわち：

```julia
FastaReader(filename) do fr
    # frからデータを読み出す、例えば
    for (name, seq) in fr
        # nameとseqを使って何かをする
    end
end
```

これにより、[`close`](@ref) 関数が呼び出されることが保証されるため、推奨されます（さもなければ、`FastaReader`オブジェクトがスコープを外れるときにファイルはガーベジコレクタによって閉じられます）。
