```
add_parameter_function(model::InfiniteModel, pfunc::ParameterFunction, 
                       [name::String])::GeneralVariableRef
```

`model`に[`ParameterFunction`](@ref) `pfunc`を追加し、印刷のために`name`を使用して、式に埋め込むことができる`GeneralVariableRef`を返します。パラメータ関数`pfunc`が`model`に属していない場合はエラーになります。`pfunc`は[`build_parameter_function`](@ref)を使用して作成する必要があります。

**例**

```julia-repl
julia> f = build_parameter_function(error, sin, t);

julia> fref = add_parameter_function(model, f)
sin(t)
```
