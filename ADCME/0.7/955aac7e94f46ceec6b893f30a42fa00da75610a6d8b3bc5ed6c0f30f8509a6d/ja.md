```
get_variable(o::Union{PyObject, Bool, Array{<:Number}}; 
    name::Union{String, Missing} = missing, 
    scope::String = "")
```

初期値 `o` を持つ新しい変数を作成します。`name` が存在する場合、`get_variable` は新しい変数を作成するのではなく、その変数を返します。
