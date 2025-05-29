契約のすべての軸を指定します。これを `AbstractVector{<:ContractAxis}` として指定したいのですが、Juliaの無限の知恵により `["a" => "b", ("c", "d")]` が `Vector{Any}` と見なされ、リテラルに型を注釈する必要があります。
