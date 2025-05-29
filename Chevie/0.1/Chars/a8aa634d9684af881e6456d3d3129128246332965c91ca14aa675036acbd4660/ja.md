`charnames(ComplexReflectionGroup or Spets;options...)` `charnames(io::IO,ComplexReflectionGroup or Spets)`

は、反射群または Spets `W` のキャラクター名のリストを返します。オプションは、特定のケースで代替名を示したり、一般的に名前の異なるフォーマットを示したりする場合があります。`IO` を引数として与える場合は、`IO` 属性によって指定できます。

```julia-repl
julia> W=coxgroup(:G,2)
G₂

julia> charnames(W;limit=true)
6-element Vector{String}:
 "φ₁‚₀"
 "φ₁‚₆"
 "φ′₁‚₃"
 "φ″₁‚₃"
 "φ₂‚₁"
 "φ₂‚₂"

julia> charnames(W;TeX=true)
6-element Vector{String}:
 "\phi_{1,0}"
 "\phi_{1,6}"
 "\phi_{1,3}'"
 "\phi_{1,3}''"
 "\phi_{2,1}"
 "\phi_{2,2}"

julia> charnames(W;spaltenstein=true,limit=true)
6-element Vector{String}:
 "1"
 "ε"
 "εₗ"
 "ε_c"
 "θ′"
 "θ″"

julia> charnames(W;spaltenstein=true,TeX=true)
6-element Vector{String}:
 "1"
 "\varepsilon"
 "\varepsilon_l"
 "\varepsilon_c"
 "\theta'"
 "\theta''"
```

最後の2つのコマンドは、スパルテンシュタインとルスティグがスプリンガー対応を説明する際に使用するキャラクター名を示しています。
