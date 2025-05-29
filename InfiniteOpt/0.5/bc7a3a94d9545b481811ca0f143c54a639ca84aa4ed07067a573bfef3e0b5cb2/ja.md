```
set_start_value_function(dref::DerivativeRef,
                         start::Union{Real, Function})::Nothing
```

`dref`の開始値関数を設定します。`start::Real`の場合、開始値は無限の範囲全体にわたって`start`になるように関数が生成されます。`start::Function`の場合、この関数は`parameter_refs(dref)`のパラメータ要素の形式に一致するサポート値引数を与えられたときにスカラー開始値にマッピングされるべきです。

**例**

```julia-repl
julia> set_start_value_function(dref, 1) # すべての開始値は1になります

julia> set_start_value_function(dref, my_func) # 各値はmy_funcを介して生成されます
```
