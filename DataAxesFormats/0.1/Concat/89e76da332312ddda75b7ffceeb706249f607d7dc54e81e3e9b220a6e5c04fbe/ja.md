すべてのマージするデータを指定します。これを `AbstractVector{<:MergeDatum}` として指定したかったのですが、Juliaの無限の知恵により `["a" => "b", ("c", "d") => "e"]` は `Vector{Any}` と見なされ、リテラルに型を注釈する必要があります。
