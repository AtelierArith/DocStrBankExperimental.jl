欠損プロパティに使用するデータを `Daf` データセットに指定します。これは、どのプロパティに値を指定するかを示す [`DataKey`](@ref) と、使用する値を指定する辞書です。これを `AbstractDict{<:DataKey, <:StorageScalarBase}` として指定したいのですが、Julia の無限の知恵により `Dict(["a" => "b", ("c", "d") => 1])` は `Dict{Any, Any}` と見なされ、リテラルに型を注釈する必要があります。

!!! note
    [`TensorKey`](@ref) は、テンソルに含まれる [`MatrixKey`](@ref) のセットとして解釈されます。これらは辞書の内部コピーで展開され、他の指定された [`MatrixKey`](@ref) を上書きします。

