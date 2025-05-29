契約のすべてのデータを指定します。これを `AbstractVector{<:ContractDatum}` として指定したいのですが、Juliaの無限の知恵により `["a" => "b", ("c", "d") => "e"]` が `Vector{Any}` と見なされ、リテラルに型を注釈する必要があります。
