```
address(n::Integer = 1; kws...)
address(options::Vector{<:AbstractString}, n::Integer = 1; level::Symbol, kws...)
address(mask::Vector{<:AbstractString}; level::Symbol, kws...)
```

`options` または `mask` に基づいて、必要な `level` に従って `n` または `length(mask)` のアドレスを生成します。例えば、`level = :country_code` とし、`options` が生成する必要のある国コードである場合、*e.g.* `["BRA", "USA"]`、期待される出力はブラジル（`"BRA"`）とアメリカ合衆国（`"USA"`）の位置に対するアドレス（それぞれの特定の形式で）だけを含むことになります。他の値は `level` として渡すことができます。

# パラメータ

  * `n::Integer = 1`: 生成するアドレスの数。
  * `options::Vector{<:AbstractString}`: 生成される可能性のある値を制限するオプションを持つベクター。
  * `mask::Vector{<:AbstractString}`: 要素ごとのオプション制限を持つマスクベクター。

# Kwargs

  * `level::Symbol = :state_code`: オプションおよびマスクベースの生成に使用されるオプションレベル。
