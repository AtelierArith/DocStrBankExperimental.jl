```
parseLine(line::String, returnPair::Bool = true)::Array{Union{String,Pair{String,String}},1}
```

g-codeの単一行を解析し、解析されたコマンドを含む`Pair{String,String}`の配列または`String`の配列を返します。

最初のコマンドは通常、何をするかを定義します（例：`G01` - 線形補間）で、続くコマンドは引数です（例：`X 14.312`）。

# 例

```julia-repl
julia> parseLine("G10 X5.Y3. E6.")
4-element Array{Union{Pair{String,String}, String},1}:
 "G" => "10"
 "X" => "5."
 "Y" => "3."
 "E" => "6."
```

文字列の配列を返す

```julia-repl
julia> parseLine("G10 X5.Y3. E6.", false)
4-element Array{Union{Pair{String,String}, String},1}:
 "G10"
 "X5."
 "Y3."
 "E6."
```
