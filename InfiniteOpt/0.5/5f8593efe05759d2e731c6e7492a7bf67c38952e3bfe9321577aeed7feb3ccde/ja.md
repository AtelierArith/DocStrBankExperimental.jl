```
set_start_value_function(vref::InfiniteVariableRef,
                         start::Union{Real, Function})::Nothing
```

`vref`の開始値関数を設定します。`start::Real`の場合、開始値は無限のドメイン全体にわたって`start`になるように関数が生成されます。`start::Function`の場合、この関数は`parameter_refs(vref)`のパラメータ要素の形式に一致するサポート値引数を与えられたスカラー開始値にマッピングする必要があります。

**例**

```julia-repl
julia> set_start_value_function(vref, 1) # すべての開始値は1になります

julia> set_start_value_function(vref, my_func) # 各値はmy_funcを介して生成されます
```
