```
read_b2_boundary_parameters(filename::String)::Dict{String, Any}
```

SOLPS入力デッキからb2.boundary.parametersファイルを読み取り、解釈します。このファイルには、コアからメッシュへの電力の交差や粒子フラックスなどの境界条件が含まれています。解釈された結果の辞書を返します。
