```
parameter_function(func::Function, 
                   pref_inputs::Union{GeneralVariableRef, AbstractArray{GeneralVariableRef}, Tuple}; 
                   [name::String = [the name of `func`]]
                   )::GeneralVariableRef
```

パラメータ関数を作成し、InfiniteOpt式に埋め込むことができる`GeneralVariableRef`を返します。これは、[`build_parameter_function`](@ref)および[`add_parameter_function`](@ref)の便利なラッパーとして機能します。さらに便利な定義方法については、[`@parameter_function`](@ref)を参照してください。

ここで`func`は、無限のパラメータを入力として受け取り（`pref_inputs`のようにフォーマットされ）、スカラー値を返す関数を示します。具体的には、`func`は次の形式である必要があります：

```
func(paramvals...)::Float64
```

ここで`paramvals`のフォーマットはポイント変数に類似しており（`parameter_refs`で与えられた無限パラメータ参照のタプルに基づきます）、`func`はスカラー数値を返す関数でなければなりません。

`func`が`pref_inputs`のようにフォーマットされたサポートを受け取らない場合、`fargs`および`fkwargs`と組み合わせてエラーが発生します。また、`pref_inputs`が無効な入力フォーマットに従っている場合もエラーが発生します。

**例**

```julia-repl
julia> p_func = parameter_function(sin, t)
sin(t)

julia> p_func3 = parameter_function((t_supp) -> 2 * sin(2 * t_supp), t, name = "mysin")
mysin(t)

julia> p_func4 = parameter_function(t, name = "mysin") do t_supp
                    if t_supp <= 5
                        return sin(t_supp)
                    else 
                        return 2 * sin(2 * t_supp)
                    end
                 end

mysin(t)
```
