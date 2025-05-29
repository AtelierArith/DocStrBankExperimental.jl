```
add_parameters(model::InfiniteModel,
               params::DependentParameters,
               names::Vector{String}
               )::Vector{GeneralVariableRef}
```

`params`を`model`に追加し、依存する無限パラメータ参照の適切なコンテナを返します。これは[`@infinite_parameter`](@ref)と共に使用するための内部メソッドとして意図されています。ただし、必要に応じてユーザーはこのメソッドを使用して`model`に`DependentParameters`オブジェクトを追加できます。ここで、`names`は各パラメータの名前を示します。

**例**

```julia-repl
julia> using Distributions

julia> dist = MvNormal(ones(3)); # 3次元

julia> domain = MultiDistributionDomain(dist); # 3次元

julia> params = DependentParameters(domain, Dict{Vector{Float64}, Set{DatatType}}(), 10);

julia> prefs = add_parameters(model, params, ["par1", "par2", "par3"])
3-element Array{GeneralVariableRef,1}:
 par1
 par2
 par3
```
