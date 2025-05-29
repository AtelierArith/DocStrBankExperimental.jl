```
Py(x)
```

`x`を`Py`型のPythonオブジェクトに変換します。

変換は[これらのルール](@ref jl2py-conversion)に従って行われます。

このオブジェクトは、属性アクセス（`obj.attr`）、インデックス指定（`obj[idx]`）、呼び出し（`obj(arg1, arg2)`）、反復（`for x in obj`）、算術（`obj + obj2`）および比較（`obj > obj2`）などをサポートします。これらの操作は、すべての引数を`Py`に変換し、`Py`を返します。
