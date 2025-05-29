```julia
read_evidence_file(
    evidence_filepath::AbstractString
) -> Tuple{Vector{Int64}, Vector{Int64}}

```

`evidence_filepath` にある観測変数と値を返します。渡されたファイルパスが空の文字列の場合、空のベクターを返します。

UAIファイル形式は次のリンクで定義されています: https://uaicompetition.github.io/uci-2022/file-formats/
